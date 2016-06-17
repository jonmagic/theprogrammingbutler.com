---
layout: post
title: Getting hacked
---

My worst nightmare happened last night, and I didn’t even know it until
late this morning. I was hacked…

### Sequence of events:

#### June 19th

-   10pm <span class="caps"><span class="caps">EST</span></span> –
    hacker figured out my email password, logged in, and sent out a mass
    email to the top 20 people on my contact list (most contacted
    people), thankfully gmail calculates this list only when you use the
    web interface in gmail, which I haven’t used in quite some time
    since I switched to using Apple Mail.app. Most everyone on the top
    20 were family or friends. Mysteriously the hacker does not send the
    mass mail to Sam or Xian, who were both on my top 20 list. The two
    people who would have known to call me (rather than email me) and
    tell me to take immediate action.
-   10:16pm <span class="caps"><span class="caps">EST</span></span> –
    Hacker? tries logging into my blog admin section from this ip
    90.194.192.57 unsuccessfully
-   10:20pm <span class="caps"><span class="caps">EST</span></span> –
    Hacker? successfully logs into my blog admin section from this ip
    88.191.47.11
-   10:23pm <span class="caps"><span class="caps">EST</span></span> –
    Magically whoever logged in at 10:20 is now logged in under a
    different ip 128.197.11.30 and figuring out my blogging system
-   10:29pm <span class="caps"><span class="caps">EST</span></span> –
    Hacker figures out my layout management system and starts adding
    javascript to my template files, first my tag.liquid file
-   10:31pm <span class="caps"><span class="caps">EST</span></span> –
    Hacker find my layout.liquid file, the master layout, and adds
    several javascript lines in there. They cause anyone who visits my
    site to get forwarded to a nasty porn storm site, and installed some
    sort of tracking js linked to cetrk.com and crazyegg? Keeps updating
    the same layout file until almost 10:33pm
-   10:34pm <span class="caps"><span class="caps">EST</span></span> –
    Still updating the same file, but from a different ip now,
    91.97.75.15, keeps updating the same file until 10:36pm.
-   10:36pm <span class="caps"><span class="caps">EST</span></span> – My
    mom emailed me that someone had control of my email. Unfortunately
    the email never got to me, because the hacker also setup my gmail
    account to forward all my mail to him, and then archive my messages
    so they bypassed my inbox (I do still have access to them, they went
    to the gmail archive folder)

#### June 20th

-   9:05am <span class="caps"><span class="caps">EST</span></span> – Sam
    calls me and leaves a message as I’m in the shower
-   9:30am <span class="caps"><span class="caps">EST</span></span> – I
    call Sam back and find out that a customer had contacted him about
    an email I supposedly sent, an <span class="caps"><span
    class="caps">NASTY</span></span> email
-   9:22am <span class="caps"><span class="caps">EST</span></span> – I
    log into my gmail and change my password
-   10:02am <span class="caps"><span class="caps">EST</span></span> –
    Finally I get to spot with my work where I can start investigating.
    Investigation shows me that the person had logged into my gmail and
    I believe only sent to the top 20 people, which was later proved
    true, at this point I just decided to start changing my password
    everywhere and send out an apology email to the people I believe got
    this nasty email
-   11:30am <span class="caps"><span class="caps">EST</span></span> – I
    call my dad to see if he and mom had got the message. He said he was
    just emailing me to let me know they had.
-   11:35am <span class="caps"><span class="caps">EST</span></span> –
    Dad calls me back to tell me my website has been hacked too. And
    its bad. He just held down the power button on his computer to get
    away from the horrible stuff that came up on his screen
-   11:43am <span class="caps"><span class="caps">EST</span></span> – I
    fix my layout.liquid file the first time, turns out I left one line
    from the hacker still in there
-   11:53am <span class="caps"><span class="caps">EST</span></span> – I
    get back into my website admin and fix the other line in
    layout.liquid
-   around 1:00pm <span class="caps"><span
    class="caps">EST</span></span> – I’m still not getting any emails,
    and its really getting to me… Finally figure out in my gmail
    settings that the hacker set all my mail to be forwarded to a
    [spam.la](http://spam.la) address, where my emails were visible to
    whole world, and skipping my gmail inbox.
-   3:38pm <span class="caps"><span class="caps">EST</span></span> – I
    figure out that my tag.liquid file also had a js line in it, so I
    fix that and thoroughly check the rest of my templates.
-   3:41pm <span class="caps"><span class="caps">EST</span></span> – I
    find the 128.197.11.30 address in my mephisto logs, track it down to
    Boston University, and immediately call their network
    operations center. I talk to one guy, then get forwarded to their
    network security department and talk to Eric. I explain to Eric who
    I am and where I’m from, and that our server had been hacked (my
    blog is on the company server) from an ip address in his network. I
    started to rattle off the ip address and he stopped me, and said
    “yeah yeah I know, we got the guy”. I said thanks and hung up.

*Moral of the story. Use a good password.*

Note: 90.194.192.57, 91.97.75.15, and 88.191.47.11 all belong to a
company in England called [<span class="caps"><span
class="caps">RIPE</span></span>](http://ripe.net/)
