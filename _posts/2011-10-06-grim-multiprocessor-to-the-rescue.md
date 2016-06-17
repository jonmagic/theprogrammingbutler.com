---
layout: post
title: Grim MultiProcessor to the Rescue!
---

We recently ran into issues with certain versions of GhostScript not
being able to convert PDF's into images. Here's how we solved the
problem.

### The Problem

Last week we launched [Speaker Deck](http://speakerdeck.com) and since
launch over 2000 people have signed up and uploaded almost a 1000
presentations. We were using GhostScript 9.04 because it is faster than
9.02 by a factor of two and fixed some processing problems we had
experienced converting certain PDFs.

```
convert: Postscript delegate failed `presentation.pdf': No such file or directory @ error/pdf.c/ReadPDFImage/663.
convert: missing an image filename `slide.jpg' @ error/convert.c/ConvertImageCommand/3011.
```

Unfortunately we ran into the same processing issue with 9.04 and thru
trial and error figured out that those presentations that wouldn’t
process with 9.04 would process with 9.02. So what to do! GhostScript
9.04 works for most presentations and is faster but fails on certain
PDFs where 9.02 actually does work.

### The Solution

We are using [Grim](http://jonmagic.com/blog/archives/2011/09/06/grim/)
to convert PDFs into images, so I decided that Grim needed to be updated
to support multiple processors. Better yet I thought it would be cool if
Grim could automatically try multiple processors if you specified more
than one, starting with the first and falling back to secondary
processors as needed.

I started working on adding Processors to Grim while at
[RubyConf](http://rubyconf.org) and Monday finished up getting it all
working. I started by pulling out the ImageMagick and GhostScript
specific code into an ImageMagickProcessor class that lets you pass in
the path to convert and gs (ImageMagick and GhostScript executables).

```ruby
Grim.processor = Grim::ImageMagickProcessor.new({:imagemagick_path => "/path/to/convert", :ghostscript_path => "/path/to/gs"})
```

Once I had that working (super easy thanks to a great test suite!) I
started in on the MultiProcessor.

The MultiProcessor accepts an array of processors and uses them in
order, falling back to secondary processors when the first in line
fails. If none of them succeed it just raises the same error the
processors on their own raise.

```ruby
Grim.processor = Grim::MultiProcessor.new([
  Grim::ImageMagickProcessor.new({:imagemagick_path => "/path/to/6.7/convert", :ghostscript_path => "/path/to/9.04/gs"}),
  Grim::ImageMagickProcessor.new({:imagemagick_path => "/path/to/6.6/convert", :ghostscript_path => "/path/to/9.02/gs"})
])
```

Monday we deployed [Speaker Deck](http://speakerdeck.com) with the
updated Grim gem and reprocessed the 13 presentations that were stuck.
Every single one of them processed without a hitch!

### The Future

Now that the actual processing logic has been split out into easy to
build Processor classes, I see us building more processors for Grim. Why
not a Quartz processor, or a processor that works on Windows.

If you would like to use Grim in your project or get involved with
development just head over to the [Grim repo on
Github](http://github.com/jonmagic/grim).
