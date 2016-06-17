---
layout: post
title: The History of Speaker Deck
---

How a product was born, from inception to implementation, and
distractions to launch.

### Inception

[Speaker Deck](http://speakerdeck.com) was born in a little Irish bar
right around the corner from our offices in South Bend Indiana in May of
2010. I was meeting
[Steve](http://orderedlist.com/the-team/#steve-smith) and
[John](http://orderedlist.com/the-team/john-nunemaker) for lunch and
they were talking about how much they disliked the slide sharing options
currently available. It was of special interest to them as they do a lot
of public speaking and at the time were teaching classes at [Notre
Dame](http://nd.edu).

They were dreaming (as they do) of a better way to share presentations
with the world. Something elegant, simple, without all the mess. Then
reality hit and they realized they just didn’t have the time to build
it. Life was too busy, family, client work, teaching, and
[Harmony](http://get.harmonyapp.com) ate up all their time, there was
just no way they could start working on a new product.

### Implementation

This was my opportunity. If I was serious about my dream of becoming a
programmer, here was my chance. I said “I’ll do it”, then cracked open
my laptop and started hacking around with ghostscript and imagemagick to
see if I could extract images from pdf’s. An hour later the core tech
([now extracted into a rubygem](http://github.com/jonmagic/grim)) behind
Speaker Deck was working (in a limited fashion) and a product was born.

June 1st of 2010 was my first git commit, a basic rails app with an
already processed presentation so I had images to use as I created the
html and css from Steve’s initial mockups. It quickly took on a life of
its own at that point, Steve implementing an awesome embeddable slide
viewer, so nifty we actually use it on Speaker Deck the same exact way
you use it when embedding a presentation on your own site.

The guys taught me test driven development while building Speaker Deck,
and over the summer and into the fall I kept working on it. Initially
just Steve and John were using it to host their slides, but then an
opportunity arose while at [Mongo
Chicago](http://www.10gen.com/events/mongo-chicago-2010), and on October
20th of 2010 we had our first beta testers signup and upload
presentations!

[![](http://jonmagic.com/assets/4e89fb7bdabe9d7909002e39/blog_post/4609508175_f3bcf70e45_b.jpg)](http://www.flickr.com/photos/johnnunemaker/4609508175/in/photostream/)\
(my coworker/boss John presenting at Mongo Chicago 2010)

### Good Distractions

Almost a year has passed since we started signing up our first beta
users and September 26th we launched Speaker Deck to the world! In the
past year I ended up going to work for Steve and John and they also
hired [Brandon
Keepers](http://orderedlist.com/the-team/#brandon-keepers) and [Matt
Graham](http://orderedlist.com/the-team/#matt-graham). In that time our
team has been doing a lot of consulting work, making our existing
product [Harmony](http://get.harmonyapp.com) better, and we even
launched [Gauges](http://get.gaug.es), a website analytics service.

The entire time we were working on these other projects we were
formulating what we wanted Speaker Deck to be and this summer that plan
started to solidify and we got back to work on it. The first big thing
that needed to happen was [moving Speaker Deck to Heroku and
S3](http://jonmagic.com/blog/archives/2011/07/27/moving-speakerdeck-to-heroku/)
for hosting.

This transition only took a few a days to initially implement but gave
us an easy & affordable way to grow the service into the future.
Meanwhile Steve went to town on some UI & UX improvements that would
help set us apart from the competition even more.

### Launch

The last month leading up to launch was pretty intense, hammering out
final details and deciding that we wanted to release the product to our
users as a free service.

Then on September 26th we launched it at about 3pm <span
class="caps">EST</span>. That first day we had over 600 signups and
hundreds of presentations were uploaded. It was a rush seeing people use
it, getting feedback, fixing bugs, and dreaming about the future.

In the past week since launch we’ve had many more signups, hundreds more
presentations uploaded, and such great feedback that has helped us
formulate an even better plan for how to move forward.

I’ll be posting more about Speaker Deck later this week, talking about
some of the triumphs and struggles we’ve had since launch.
