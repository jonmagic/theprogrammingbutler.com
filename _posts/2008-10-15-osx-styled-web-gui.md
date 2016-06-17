---
layout: post
title: OSX Styled web gui
---

I’ll probably get in trouble for this, but I decided to [release
it](http://github.com/jonmagic/webapp_gui/) anyways… I’ve been working
on some software for running my company and needed a nice gui,
implemented in html/css/js. I decided, since I prefer using osx over any
other interface, I wanted my web app to look like osx too.

So I started from scratch and made up this gui using minimal html
markup, simple css (I use the [blueprint](http://www.blueprintcss.org/)
css library as a foundation), the [jquery](http://jquery.com) javascript
library (including jquery ui elements), and the [famfamfam
silk](http://www.famfamfam.com/lab/icons/silk/) icon set.

This is not <span class="caps"><span class="caps">TOTALLY</span></span>
osx themed, as I couldn’t find an tabs anywhere in osx that worked for
web apps (at least not easily implemented ones), so I used the jquery
tabs instead and just made them match as close as possible to the rest
of the theme.

#### Caveat

This will not work in IE (i’m pretty sure, but haven’t tested), but it
does work in modern versions of webkit based browsers (Safari and
Chrome) and Firefox.

[Here is the link to my github
repo](http://github.com/jonmagic/webapp_gui/tree/master)
