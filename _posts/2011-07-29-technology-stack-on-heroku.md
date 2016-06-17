---
layout: post
title: Speaker Deck's Technology Stack
---

Ever curious about what the software stack for programs you use looks
like? I am, so I thought I'd share what Speaker Deck's technology stack
looks like right now, and then I can look back a year from now and see
how much it has changed.

[Speaker Deck](http://speakerdeck.com) is a simple application. You
upload a pdf of a presentation that has been exported from Keynote,
Powerpoint, or something similar, and it turns it into a deck of images
that are easily viewed thru an HTML5 slide browser.

### High-Level

So what makes it tick? Here’s the rundown from a high level:

-   html/css/javascript: currently we don’t use Flash anywhere
-   [Ruby on Rails](http://www.rubyonrails.org) web framework
-   A bunch of ruby gems which I’ll list below
-   [MongoDB](http://mongodb.org), a high-performance document-oriented
    database
-   [Redis](http://redis.io/) is an advanced key-value store
-   [<span class="caps">FOG</span>](http://fog.io) is technically a ruby
    gem, which get their own section below, but had to mention it here
    as it makes storing files in the cloud super easy

### Service Providers

Platform as a service and software as a service providers:

-   [Heroku](http://heroku.com) is a platform for easily and quickly
    deploying, hosting, and scaling applications built on Ruby, Node.js,
    and now Clojure. A simple “git push heroku” lets us deploy to
    the cloud.
-   [MongoHQ](http://mongohq.com) is where we host our MongoDB database.
    They manage the servers so we don’t have to.
-   [Redis To Go](http://redistogo.com/) is a hosted Redis
    database solution. We use Redis for job queues and Redis To Go lets
    us quickly scale our database to meet our needs at the time.
-   [Amazon Simple Storage Service](http://aws.amazon.com/s3/),
    otherwise known as Amazon S3, is a quick and easy way for us to host
    thousands of slides and pdf’s without going broke. They charge by
    the gigabyte for bandwidth and storage and its darn cheap.

### Ruby Gems

-   [rails 3.1](https://github.com/rails/rails/tree/3-1-stable)
-   [json](http://flori.github.com/json/)
-   [sass-rails](https://github.com/rails/sass-rails)
-   [coffee-rails](https://github.com/rails/coffee-rails)
-   [uglifier](https://github.com/lautis/uglifier)
-   [jquery-rails](https://github.com/rails/jquery-rails)
-   Nunemaker’s fork of [imanip](https://github.com/jnunemaker/imanip)
-   [RedCloth](https://github.com/jgarber/redcloth)
-   [canable](https://github.com/jnunemaker/canable)
-   [faraday](https://github.com/technoweenie/faraday)
-   [mash](https://github.com/mbleigh/mash)
-   [mongo\_mapper](https://github.com/jnunemaker/mongomapper)
-   [scam](https://github.com/jnunemaker/scam)
-   [will\_paginate](https://github.com/mislav/will_paginate)
-   [fog](http://fog.io)
-   [carrierwave](https://github.com/jnicklas/carrierwave)
-   [mm-carrierwave](https://github.com/80beans/mm-carrierwave)
-   [resque](https://github.com/defunkt/resque)
-   [hunt](https://github.com/jnunemaker/hunt)
-   [newrelic\_rpm](http://rubygems.org/gems/newrelic_rpm)
-   [exceptional](http://rubygems.org/gems/exceptional)

There are a few more pieces of software we use for testing but this post
is already getting kind of long.

So what are you using in your software stack?
