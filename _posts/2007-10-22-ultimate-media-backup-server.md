---
layout: post
title: Ultimate media/backup server
---

I’ve been using a winxp box in my living room for some time now, and
while it works really well, I do find it lacking. Currently it has a
200gb hdd and a 80gb hdd, runs xp pro, has a video card with composite
out so i can go straight to the tv, has
[Azureus](http://azureus.sourceforge.net/) and
[ted](http://www.rulecam.net/ted/) to get tv shows,\
[k-lite codec pack](http://filehippo.com/download_klite_codec_pack/)
with Media Player Classic, and vnc so I can remote control it… Its
pretty slick over all, but I’m running out of storage and I want
something with more features.

#### So here are my new requirements:

-   Easily expandable storage, without reinstalling my os or adding raid
    cards etc…
-   Smaller form factor, my current machine is a full desktop tower
-   IR remote control and <span class="caps"><span
    class="caps">VNC</span></span>
-   auto download shows
-   act as a backup resource for all my computers in the house, which
    means it has to have redundant storage
-   looks pretty, both hardware and software

*Well, the only way I know how to meet those requirements is with a [Mac
Mini](http://www.apple.com/macmini/) and a
[Drobo](http://www.drobo.com/) storage device.*

#### How I’ll pimp the Mac Mini

I’ll need at least a gig of ram in the mini, doesn’t matter how big its
hdd is though since the Drobo will be plugged into it. I’ll run Leopard
with [Azureus](http://azureus.sourceforge.net/) and
[ted](http://www.rulecam.net/ted/) to get my tv content. I’ll setup
<span class="caps"><span class="caps">AFP</span></span> and <span
class="caps"><span class="caps">SMB</span></span> file sharing on it so
I can access this baby over the network. I’m not sure yet how I’ll
remote control, might use <span class="caps"><span
class="caps">VNC</span></span>, might not???

#### What I’ll do with the Drobo

The drobo will be attached to the mini via usb 2.0. I’ll probably start
with a few 250gb or 500gb drives, doesn’t matter cuz of the drobo’s
magic!!! With the advent of Leopard and Time Machine I’ll be able to set
this as a backup drive over the network for all my Mac’s, never having
to worry about data loss again! I’m so excited about this part of it.

Anyways, there are more details to figure out, and of course I need to
find funding ;-) But one can always wish can’t they…
