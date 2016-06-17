---
layout: post
title: Best phone system for a small business, Part 1
---

This article is for small business owners, and even better, for their IT
guy/gal… If you are looking at upgrading your phone system, and want to
upgrade inexpensively but have a clear upgrade path for the future, I’m
going to outline how to build what I believe to be the most cost
effective, easy to maintain, pbx based phone system available.

The pbx itself is based on PC hardware, with a special card for
interfacing with the telco (<span class="caps">ATT</span>, Verizon,
etc), and a software stack called [<span class="caps"><span
class="caps">PBX</span></span> in a Flash](http://pbxinaflash.net/).
<span class="caps"><span class="caps">PBX</span></span> in a Flash
(PiaF) was put together [by a few
gentlemen](http://pbxinaflash.net/about/) looking for a solid software
stack for their telephony needs. Here is what is in the stack:

-   [CentOS](http://www.centos.org/) for the OS that everything lies on
    top of.
-   [Asterisk](http://www.asterisk.org/) for the <span
    class="caps"><span class="caps">PBX</span></span> stack.
-   [FreePBX](http://www.freepbx.org/) helps in configuring and
    maintaining the Asterisk configuration.
-   Prebuilt scripts, for configuring everything from dhcp to cisco
    phones

For phone hardware I’ve used Cisco, Linksys, and
[Aastra](http://www.aastra.com/). Aastra seems to be the recommended
brand of late, for features, price, and ease of configuration. I’m not a
huge fan of the Cisco phones (overpriced and they seem to cripple their
<span class="caps"><span class="caps">SIP</span></span> firmware), but
Cisco’s economical product line, Linksys, makes some great phones.

Well, there’s the intro for you, if you want to learn more, read on!

I’ve done phone systems for businesses that only need 2 or 3 phones, and
systems for companies with 20+ extensions. I’m comfortable recommending
this system for a business with up to 100 extensions, more than that and
you might want to look at having dual load balanced servers.

For this setup I’m going to describe below, we’ve got a business with
around 30 employees, 20 of which have their own extensions on the phone
system. There is a sales group, support group, and various
administrators, as well as production staff.

Any \$400 to \$600 PC will work for our base system. 2.0ghz+ Intel or
<span class="caps"><span class="caps">AMD</span></span> processor, at
least 1gb of ram (I put in 2gb since its so cheap). Looking for hardware
with a good warranty? Check out my company [SabreTech Consulting <span
class="caps"><span
class="caps">LLC</span></span>](http://www.sabretechllc.com) for some
great PC’s. We ship anywhere in the US (and actually, a lot of our PC’s
are overseas as well, thru an associate of ours).

Let me back up for a second and explain the two ways we can get “dial
tone” to our phone system (i.e. be able to make calls to the outside
world). Way \#1, use land lines thru your local telco, for example <span
class="caps"><span class="caps">ATT</span></span> or Verizon. Way \#2,
use voip trunks thru any of hundreds of carriers, this method requires a
<span class="caps"><span class="caps">NICE</span> <span
class="caps">SOLID</span></span> internet connection. Depending on your
area and telco providers, it may or may not be more cost effective to
use land lines thru the telco. These days I’ve found that its usually
cost effective to have enough land lines, with “unlimited” long
distance/local packages on them, for your average use (sum of the number
of lines you use every minute of the day, divided by the number of
minutes they are in use), and then voip trunks for “peak” times when you
need Just A Little More, and for international calls.

So, we’ve figured out that our average use is 4 to 6 lines in use at any
given minute (this is just calls to the outside world, does not include
internal calls, i.e. extension to extension). So we want to get 6 lines
with unlimited local and long distance packages, which ends up costing
about \$456 a month. So how do we get these phone lines into our phone
system?

Ok, time to step back again and explain the two ways the phone company
can get us a line, digital or analog. Analog lines are the ones we had
when we were growing up, you know, the phone on your wall in the kitchen
:-) These analog lines are also called [pots
lines](http://en.wikipedia.org/wiki/Plain_old_telephone_service).
Digital lines, a.k.a. [<span class="caps"><span
class="caps">PRI</span></span>’s](http://en.wikipedia.org/wiki/Primary_rate_interface),
usually come in bundles of 23. In some areas you can get “partial” <span
class="caps"><span class="caps">PRI</span></span>’s, and if you can in
your area, and the price is right, <span class="caps">DO IT</span>…
Digital lines will be better quality and give fewer headaches than
analog lines. The nice thing about digital lines is they either <span
class="caps"><span class="caps">WORK</span></span> or the <span
class="caps"><span class="caps">DON</span></span>’T <span
class="caps"><span class="caps">WORK</span></span>, there’s not much
in-between. Analog lines on the other hand, can have a myriad of
problems, including dropped calls, static, etc. Analog lines can work,
even if the connection is crappy, and therefore its harder to convince
the telco that there might be a problem with the line.

So, I want some lines from my telco, but I need to get them <span
class="caps"><span class="caps">INTO</span></span> the phone system! My
absolute favorite company for doing this is [Rhino
Equipment](http://www.rhinoequipment.com/). They make a series of analog
and digital interface cards. These cards <span class="caps"><span
class="caps">ARE</span> <span class="caps">NOT</span> <span
class="caps">CHEAP</span></span>, <span class="caps">BUT</span> they are
worth every penny and more. In fact, I would pay twice the price they
charge for them, and here is why: they have the best tech support I have
ever used in my life. Let me repeat that. <span class="caps"><span
class="caps">THEY</span> <span class="caps">HAVE</span> <span
class="caps">THE</span> <span class="caps">BEST</span> <span
class="caps">TECH</span> <span class="caps">SUPPORT</span> ON <span
class="caps">THE</span> <span class="caps">PLANET</span></span>. These
guys have helped me time and time again, always courteous and patient.
On one job they worked with me for 3 days trying to troubleshoot dropped
calls, and said on day 2 that it wasn’t their equipment, but instead the
phone company, but they stuck in there <span class="caps"><span
class="caps">RIGHT</span> TO <span class="caps">THE</span> <span
class="caps">END</span></span>. They kept helping me, even after they
knew it was the phone company and not their equipment causing problems,
and if it weren’t for them, I never could have convinced the phone
company to get their act together and fix the lines.

For most small businesses, where I can’t get a <span class="caps"><span
class="caps">PRI</span></span>, only pots lines, I use the [Rhino <span
class="caps">R8FXX</span>-EC
card](http://www.rhinoequipment.com/R8FXXcard.html). It can support up
to 4 fxo (or fxs) modules on it. Each fxo module can handle 2 pots lines
from the telco. This card has built in echo cancellation, just one more
reason its worth every penny. For this example, since we’re going to
have 6 lines, I need to get the Rhino card with 3 modules on it.

Ok, we’ve got our PC, we’ve got our interface card to interface with the
telco, now we just need to pick a phone model to get everyone. I’m going
to have to go with [this
recommendation](http://nerdvittles.com/index.php?p=207), the [Aastra
57i](http://www.aastra.com/cps/rde/xchg/SID-3D8CCB6A-BC5ACAC2/04/hs.xsl/19703.htm).
I have yet to get this particular model in to try myself, but I trust
Ward Mundy with my life, so what he says, goes :-)

Well, two pages in and I’ve decided to split this into a multi part
article. We’ll call this Part I. Please keep checking back for Part II,
where I’ll cover installing and configuring the software stack and your
Rhino card.
