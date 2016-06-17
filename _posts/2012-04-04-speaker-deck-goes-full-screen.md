---
layout: post
title: Speaker Deck Goes Full-screen
---

I'm really excited to let you know that we've added full-screen support
to presentations on [Speaker Deck](http://speakerdeck.com). This feature
has been percolating for awhile, going thru several iterations before we
found a solution that we really liked.

We are using the [new full-screen
API’s](https://developer.mozilla.org/en/DOM/Using_full-screen_mode)
available in Webkit based browsers and Firefox. There were a few
obstacles we had to overcome, mostly just learning how the API’s
actually worked, specifically how to make an element inside an iFrame go
fullscreen (make sure to add the allow flags to your iframe tag).

In the process we learned a ton of great stuff that will let us do some
pretty cool things in the future. The way we designed full-screen will
let us use higher resolution slides in the future as well (you know, in
case we decide to start encoding them at the resolution of that new
device Apple just released).

Here’s a presentation I did awhile back, check it out in full-screen!
