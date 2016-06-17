---
layout: post
title: Integrating with Quickbooks
---

If you are a software developer working on software for small to medium
businesses, then there is a 70% chance (my unscientific calculation)
that you’ll run into Quickbooks at some point.

If you want to integrate with Quickbooks, and especially if you are a
developer using ruby, then this post will point you in the right
direction for getting things done. So please, read on :-)

**<span class="caps"><span class="caps">DISCLAIMER</span></span>:** I am
a former associate of Daniel (and
[BehindLogic](http://www.behindlogic.com)) and I got a freebie for
writing this post (which is cool cuz I was gonna write it anyway, but
don’t tell him)…

I’ve been working on writing
[software](http://jonmagic.com/programming/suite) to manage our small IT
consultancy, [SabreTech Consulting <span class="caps"><span
class="caps">LLC</span></span>](http://www.sabretechllc.com) and the
time came to be able to integrate with our accounting package,
Quickbooks. Awhile back we had tried, unsuccessfully, and so I was not
looking forward to it this time around.

But, a friend of mine has been working on writing a [Quickbooks
gem](http://www.behindlogic.com) and recently released it to the wild,
so I thought I would take a crack at the problem again.

After getting the gem from him (\$199) and the http adapter to sit on
our PC that runs quickbooks (\$25) I was up and running within minutes.
I included the gem in my rails app, fired up my app console, and started
creating QB objects and saving them.

In about 5 hours of work last week I was able to build an interface to
easily link clients in Suite to clients in Quickbooks <span
class="caps"><span class="caps">AND</span></span> make it so when you
create a new client in Suite it can automatically create the client in
Quickbooks, and populate the phone/email/address fields. Having
completed this in such a short time I was feeling pretty good! Working
with Quickbooks wasn’t a hassle anymore, so I decided that this week I
would tackle turning our completed tickets in Suite (work orders) into
invoices in Quickbooks.

In just 2 days (really fast for me, I’m a slow slow slow programmer) I
had wired up an Invoice model in my rails app, had it creating an
invoice in quickbooks and putting in the line items for labor, with
quantities and descriptions, setting the thank you message at the bottom
of the invoice, and setting the “IsToBePrinted” field so that our
manager can just click on File &gt; Print Forms &gt; Invoices in
Quickbooks and turn all those invoices into paper :-)

Basically I was able to cut down 3 to 5 minutes of work (for our
manager) to a button press and 20 to 60 seconds of server work. That is
a time savings (via integration) that most businesses would kill to
have.

Now, while I’m super excited about all this, there were some downers
(please fix these Dan!):

-   Documentation is very sparse and sometimes incorrect, I’ve actually
    offered to help him on it
-   There are some bugs in the gem. One I found was when creating an
    invoice and setting the quantity field for a line item, it wouldn’t
    accept a float, only integers. Daniel replied to my emails within 12
    hours, and showed me what to fix in the gem, and said he would fix
    it soon in the gem and re-release the gem to everyone who had
    bought it.

All said and done, I highly recommend the [Quickbooks gem by Daniel
Parker of BehindLogic](http://www.behindlogic.com).
