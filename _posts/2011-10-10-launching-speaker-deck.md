---
layout: post
title: Launching Speaker Deck
---

Looking back at the last two weeks since launching Speaker Deck.

### Launching

Knowing when to launch a product is a painstaking task and ultimately
you are never sure if its the right time, but at some point you have to
pull the trigger. September 26th [we](http://orderedlist.com/the-team/)
finally committed and launched [Speaker Deck](http://speakerdeck.com) to
the world.

The past two weeks since launch have been pretty intense, we’ve had over
2500 signups and over 1000 presentations uploaded. We’ve received
hundreds of emails, people just telling us how excited they are about
Speaker Deck and many of them asking for a feature or requesting help.
Seeing everyone’s reactions has confirmed in our minds that we weren’t
the only ones feeling severe slide hosting pain.

The [twitter search for
speakerdeck](http://twitter.com/#!/search/speakerdeck) has seen a
constant stream of tweets, almost all of them linking directly to
specific slide decks, which is awesome!

### Fixing

Thankfully [Heroku](http://heroku.com) has been a fantastic platform for
Speaker Deck so far. During peak traffic we’ve been able to easily scale
up both our web capacity (how many requests we can handle from your
browsers) and the background worker capacity (where we process your PDFs
into individual slides).

No story is complete without some drama though right? When we opened up
signups we almost immediately began seeing presentations that wouldn’t
process. Thankfully within a week we were able to [roll out
fixes](http://jonmagic.com/blog/archives/2011/10/06/grim-multiprocessor-to-the-rescue/)
that got us past this hurdle.

We also ran into problems with slides acting like they were never
processed even though they had. This turned out to be race conditions.
In addition, there were issues with caching. There were a couple
instances where we cached something and then missed clearing that item
from the cache when the item was updated. Hard bugs to track down but
easy to fix thankfully.

All in all things went really well, thankfully, since we were all gone
to New Orleans for [RubyConf](http://rubyconf.org) and without good
internet. Looking back, launching 2 days before a road trip was probably
not the wisest thing we’ve ever done.

### Future

I’m betting many of you are thinking “how the heck is this sustainable?”
I’ll let you know when we figure it out. Seriously though, we do have
plans to monetize and I’d like to start talking about them to see what
you folks think.

The first idea is just what we’re doing right now, mentioning our other
products ([Gauges](http://get.gaug.es) &
[Harmony](http://get.harmonyapp.com)) in a very small and tasteful way
in the sidebar. For this plan to succeed on its own there would have to
be a lot of people clicking through and signing up for our other
products.

The second plan is to add pro accounts. We’ve heard a lot of great
feedback about bigger features people want, like private presentations
that you can share with a select group and also statistics. We’d love to
hear more about features you want, especially the ones you’d be willing
to pay for.

We of course still have a lot of core features to build, like search,
full screen mode, following presenters, activity streams, and so much
more.

### Conclusion

All of us at Ordered List just want to say thanks. It has been a wild
ride and we’ve been blown away by how many people are using Speaker Deck
and all the good will that has been coming our way. Thank you for making
it a success!
