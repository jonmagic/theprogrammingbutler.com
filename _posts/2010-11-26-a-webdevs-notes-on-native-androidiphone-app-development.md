---
layout: post
title: A WebDev's notes on native Android/iPhone app development
---

I was contracted to build a fairly simple phototherapy treatment time
calculator app for one of our clients recently, and in the process
learned A LOT about developing for the iPhone and Android using
html/css/javascript.

The requirements for the job were that the final app feel native and
that it be able to be purchased on the respective market place (Appstore
or Android Market).

I’d already written the [app once for the
iPhone](http://itunes.apple.com/us/app/daavlin-phototherapy-dose/id386168638?mt=8),
using the [jqTouch](http://www.jqtouch.com/) library and then wrapping
the whole thing with [PhoneGap](http://www.phonegap.com/), but this time
around the client wanted to add some features that made me look further
than jqTouch.

Initially I fantasized about a write once deploy twice approach using
something like [Appcelerator
Titanium](http://www.appcelerator.com/products/titanium-mobile-application-development/).
The more I read however the more I realized no matter how I went about
this project I was going to end up with more than one codebase, one for
the iPhone and at least one for the Android. I decided to go ahead with
Appcelerator however and developed for the iPhone first. One of the
biggest things I was looking for was a native bottom tab bar for
navigating between the different phototherapy calculators (<span
class="caps">UVB</span>, <span class="caps">UVA</span>, UVA1, and Blue),
and Appcelerator let me quickly build a native, beautiful, functional
app that exactly fit the clients needs.

After a bit of troubleshooting I had it deploying to my actual iPhone,
but no matter how hard I tried I could never manage to get it to deploy
to the Android emulator.

Next I started working on a [Sencha
Touch](http://www.sencha.com/products/touch/) version of the app, which
I planned to wrap with PhoneGap, but after about an hour of digging
around in Sencha I decided it didn’t fit my programming aesthetic. I
also talked to someone who wrote an app in Sencha and they said it had a
ways to go with speed, animations were still jerky on older hardware.

Finally I decided to give [JqueryMobile](http://jquerymobile.com/) a try
(thanx Xian!) and it was a great fit for a webdev like me. Using the
latest PhoneGap and JqueryMobile I had the app rewritten and running on
the Android Emulator in just under 2 hours, and then another 2 hours
tweaking the interface and interactions. If you know
html/css/javascript, you can write a fairly native feeling app in no
time with JqueryMobile.

Having used jqTouch, Appcelerator, JqueryMobile, PhoneGap, and having
looked at Sencha, I have to say Appcelerator was by far the best
experience. I enjoyed programming the interface rather than laying out
the html and then styling it with <span class="caps">CSS</span>. I
enjoyed how quickly and easy it was to deploy to the iPhone (I wish it
could do the same for Android!). Most of all I loved how it built a
native interface, which beats an html5 interface almost every time in my
opinion.
