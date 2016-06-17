---
layout: post
title: Compiling Executables on Heroku
---

Are you using Heroku and want to run a program not included in the
Heroku environment? I'm going to show you how.

For [Speaker Deck](http://speakerdeck.com) we wanted to be able to
extract the text from uploaded pdf’s so that we can index them and make
them searchable, but the program we’d been using to do this on our dev
machines, pdftotext (part of the [<span
class="caps">XPDF</span>](http://foolabs.com/xpdf/) library), wasn’t
available on our [Heroku](http://heroku.com) instances.

On a whim I typed “heroku run bash” and sure enough I was dropped into a
bash shell with our Heroku Cedar Stack instance.

```bash
heroku run bash
```

Then I went into our apps tmp directory and tried a wget with the xpdf
url, but it failed so I tried curl with the -o option to output to file
and it worked. Then I unzipped the file and started building it!

```bash
curl ftp://ftp.foolabs.com/pub/xpdf/xpdf-3.02.tar.gz -o xpdf.tar.gz
tar zxvf xpdf.tar.gz
cd xpdf-3.02
./configure
make
```

When it was done building I found the executable we needed, pdftotext,
sitting in the xpdf build directory. I scp’d it to my machine, created a
bin directory in our apps folder, and stuck the executable there. Then
with a quick git commit and git push to Heroku we were in business!

If I had an environment locally that was identical to the Heroku
instance I could have built it locally, but to ensure it was built to
run on the Heroku instance it just made sense to build it there in the
first place.

The bin directory was added to the apps path automatically so I was able
to execute the pdftotext program from inside our Rails app without a
hitch.

**Update:** Josh Peek commented on the [Hacker News
post](http://news.ycombinator.com/item?id=2816783) that he bundled the
xpdf source in a [gem which compiles itself at
runtime](https://github.com/josh/ruby-xpdf)… Probably a better longterm
solution as it works if the underlying environment changes enough to
break a prebuilt binary.
