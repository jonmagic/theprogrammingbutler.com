---
layout: post
title: Stalled Web Dynos on Heroku
---

What do you do when your app on Heroku is dropping requests like your
dad does puns? Let me show you!

First off some sage advice from Douglas Adams.

Three deep breaths thru your nose and lets get to work. Pull up your
terminal and from your project directory run the following command to
get log entries of requests that are timing out:

```bash
heroku logs --tail | grep timeout
```

This will filter your apps logs for the word timeout, which means you’ll
get just the lines you need to diagnose if one of your web dynos is more
troublesome that the others. Start scanning for lines like this:

```bash
2011-09-12T17:08:01+00:00 heroku[router]: Error H12 (Request timeout) -> GET http://yourdomain.com dyno=web.3 queue= wait= service=30000ms status=503 bytes=0
```

You’ll notice about halfway thru where it says “dyno=web.3”. See if
there is a pattern of a specific dyno having more timeouts than any
others. If you identify one as being the primary culprit its a quick
command to get it fixed:

```bash
heroku restart web.3
```

Rinse and repeat. Keep an eye on the logs, filtering for just what you
are looking for. Restart any dynos causing issues. Rule the world!

### Epilogue

So how did we figure this out? One of our products, [Speaker
Deck](http://speakerdeck.com), started getting hammered Friday and when
we went to scale up the number of web dynos it seemed like it hurt
rather than helped.

I started tailing the logs, found the timeout errors, then focused in on
them and identified one web dyno as being flaky. Restarting that one
dyno had us back up and running and serving hundreds of pages per
minute.
