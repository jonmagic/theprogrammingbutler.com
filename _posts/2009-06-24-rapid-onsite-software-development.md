---
layout: post
title: Rapid Onsite Software Development
---

My uncle has been bugging me to help him with writing some software for
awhile now, and this last weekend he sent me another email with a new
idea, to help him in his business. I had some time available this week,
so I decided to drive down to his shop and try something. My goal was to
take his simple idea, boil it down to its essence, and write the whole
application in a day using [Rails](http://www.rubyonrails.com).

To prepare myself I started working on [<span class="caps"><span
class="caps">TDD</span></span>](http://en.wikipedia.org/wiki/Test-driven_development)
again, using [shoulda](http://thoughtbot.com/projects/shoulda/) and
[factory\_girl](http://thoughtbot.com/projects/factory_girl). I also
built my own version of
[bort](http://github.com/fudgestudios/bort/tree/master) from the ground
up, called [pudding](http://github.com/jonmagic/pudding/) (it has a
couple flavors, including
[vanilla](http://github.com/jonmagic/pudding/tree/vanilla) and
[tapioca](http://github.com/jonmagic/pudding/tree/tapioca)). I tried to
find the right mix of features to give myself a running start when I
arrived onsite.

I arrived at 8:30am this morning and started programming at 9am. At
first things were going fairly well, building my models out using <span
class="caps"><span class="caps">TDD</span></span> went fast, and I was
rolling along nicely on writing my controllers using <span
class="caps"><span class="caps">TDD</span></span> when I hit a wall,
aka, lack of knowledge on my part. After hitting this wall for 45
minutes I finally gave up on <span class="caps"><span
class="caps">TDD</span></span> and just went back to my old way of doing
things, i.e. no testing.

I was back on a roll again, using my [osx
theme](https://github.com/jonmagic/webapp_gui/tree) for the admin
interface, and [blueprint](http://www.blueprintcss.org/) for the css
reset, typography, and layout on the technician facing part of the
application (the part that will be used the most).

Things were going along nicely until I ran into issues with the way I
was doing ajax modals, via [thickbox](http://jquery.com/demo/thickbox/).
I’d already implemented quite a bit using thickbox, when I decided I
needed to start over on my modals using a different library. So far I
think I’m gonna use [jqModal](http://dev.iceburg.net/jquery/jqModal/).

So, at 4:30pm I called it quits for the day, realizing my “app in a day”
dream was not gonna happen, although I believe I’m about a 1/3rd of the
way there, which isn’t too bad.

### Lessons learned?

-   I need to work quite a bit more on testing, I need to know it like
    the back of my hand
-   I need to have a sample controller built out in my pudding apps, so
    I can do a bit of copy/paste when building my controllers
-   It would also be nice to include my osx theme, and blueprint theme
    in my pudding apps
-   I need to get better at jQuery, and find the best plugins for my
    different needs

