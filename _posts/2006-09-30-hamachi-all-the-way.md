---
layout: post
title: Hamachi all the way...
---

Ok, I’ve been following the development of Hamachi, a.k.a. way to darn
easy <span class="caps"><span class="caps">VPN</span></span> for a
couple months now… Well I finally started using it today and I’ve got to
say… <span class="caps"><span class="caps">WOW</span></span>, that was
way to easy…

But thats the way we like it around here, things so easy that you don’t
have to even think about them, they just work…

Wondering what the heck I’m talking about yet? Here’s the deal:

-   Fact1 – <span class="caps"><span class="caps">VPN</span></span>
    stands for Virtual Private Network.
-   Fact2 – What <span class="caps"><span class="caps">VPN</span></span>
    really means is, I can connect 2 or more computers together, no
    matter how far the are apart, and they’ll think that they are
    sitting right next to eachother and talk their little computer
    langauge to their hearts content.\
    -   For example: I have a computer in Michigan and my friend has a
        computer in California and we want to share files with
        eachother, share eachothers printer, share music, etc… But how
        can we do this securely without anyone evesdropping and stealing
        our stuff? With a <span class="caps"><span
        class="caps">VPN</span></span> of course…
    -   Does it make sense yet?
-   Fact3 – <span class="caps"><span class="caps">VPN</span></span>’s
    have not been the easiest thing to configure for a number of years,
    and therefore were not used, or were used and cost a lot of money…
-   Fact4 – Today that has changed…

If you go to [Hamachi’s Website](http://hamachi.cc) you can download
Hamachi for Windows or Linux and install it and use it inside of 2
minutes. If you use an [Apple Computer](http://www.apple.com) running
<span class="caps"><span class="caps">OSX</span></span> then you’ll want
to head over to this forum and check it out, or just continue reading as
I’m going to give my own little How-To…

1.  First, go to [This
    Website](http://www-user.rhrk.uni-kl.de/~nissler/tuntap/) and
    download the tuntap that is appropriate for your version of <span
    class="caps"><span class="caps">OSX</span></span>.
2.  Second, once that file is downloaded open a Terminal session and
    browse to \~/Desktop (or wherever you just downloaded that file to).
3.  Tyoe\
    -   tar zxvf tuntap\*.tar.gz

4.  Now go to Finder and double click the “tuntap\_installer.pkg” icon
    and follow the directions
5.  Go to [This Website](http://files.hamachi.cc/osx) and download the
    latest version of Hamachi for <span class="caps"><span
    class="caps">OSX</span></span>.
6.  Open the Terminal again and browser to wherever you downloaded the
    hamachi file to.
7.  Type\
    -   tar zxvf hamachi-0.9.9.9-12-osx.tar.gz

8.  Now in your terminal type\
    -   sudo tuncfg

9.  In Finder find the hamachi file you just expanded, look in the new
    folder that was created
10. Open the <span class="caps"><span class="caps">README</span></span>
    and follow the directions from there and you’ll be up and running in
    no time :-)

