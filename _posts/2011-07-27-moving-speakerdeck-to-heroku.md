---
layout: post
title: Moving Speaker Deck to Heroku
---

While at RailsConf earlier this year we decided that it would be wise to
move Speaker Deck to Heroku and S3, and we finally made it happen.

### History

[Speaker Deck](http://speakerdeck.com) has been my labor of love since
June 1st of last year.
[Steve](http://orderedlist.com/the-team/#steve-smith) and
[John](http://orderedlist.com/the-team/#john-nunemaker) had the idea and
I set about making it happen in my spare time. It launched October 20th
2010 (with a lot of help from Steve and John) and has been purring along
quietly since then. We’ve had 38 people request beta signups and as of
today 85 presentations have been uploaded.

### Getting Started

So back to point of this post, we decided that this app, with its hunger
for lots of background workers (to process slides) and its desire to
scale as adoption grows, mandated that we figure out a scaling strategy
that worked for the app, and worked for us and our resources at the
moment.

We had been tossing [Heroku](http://heroku.com) around in the back of
our minds for awhile and after talking to a couple of the Heroku guys at
[RailsConf](http://railsconf.com) and having them check if their system
had some software we needed (imagemagick/ghostscript), we decided to
give it a go.

Just a few days ago I decided to get to work on it after talking to my
coworkers about how to make it happen.
[Brandon](http://orderedlist.com/the-team/#brandon-keepers) and I dug in
and implemented storing slides on S3 (instead of MongoDB’s gridfs) in
just a few short hours thanks to the
[Carrierwave](https://github.com/jnicklas/carrierwave) gem.

It just so happened that this weekend was the [Rails 3.1
hackfest](http://weblog.rubyonrails.org/2011/7/14/rails-3-1-hackfest),
so Saturday we upgraded the app to Rails 3.1 and then to use Ruby 1.9.2
so it could run on the [Heroku Cedar
Stack](http://devcenter.heroku.com/articles/cedar). Next we started
working on deploying to Heroku.

### Deploying

Deploying ended up being a lot of trial and error. First I ran into an
issue with Heroku’s bundler version (a release candidate) not being able
to find one of my dependencies, but that was solved with the handy
“bundle cache” command. You just do “bundle cache” and then check
vendor/cache into your repo and it sends all the gems up (still in the
compressed gem form) so bundler can install them from the vendor/cache
dir.

Finally I couldn’t get my resque workers to run in the right
environment, turns out I was missing “task ‘resque:setup’ =&gt;
:environment” in my Rakefile. Hadn’t needed that on our previous deploy
to [Linode](http://linode.com), so it took awhile for me figure that one
out.

### Migrating

Brandon and I wrote a script to migrate the data on the old Linode
server to our local database and at the same time suck the pdf’s out of
Mongo on the old server and then put them on S3 rather than keeping them
in gridfs. Then a quick mongodump and mongorestore later our production
data was synced from my local machine to our new MongoHQ database.

Now that the pdf’s were on S3 and the mongo database was populated we
just had to reprocess the pdf’s into slides. Technically we could have
grabbed the already generated slides from the old server, but we really
wanted to see how much we could scale our worker processes on Heroku.

Here’s the fun part! After a few failed starts (I’ll talk about those in
a minute) we had 100 heroku workers processing 5000 slides (an intensive
imagemagick/ghostscript task) and it ripped thru them all in just a few
minutes. It was awesome to watch the resque web console and typing
“heroku ps:scale worker=100” was a lot of fun!

### Heroku Scaling Gotchya’s

DO <span class="caps">NOT</span> remove workers while you are processing
a bunch of stuff unless your jobs are easy to restart. Heroku kills the
processes not caring if they were already working on something, leaving
jobs in limbo :/

DO <span class="caps">NOT</span> change (upgrade/downgrade) your
RedisToGo plan while workers are running, your redis db gets replaced
instantly, losing any currently processing jobs.

### Wrap Up

Overall this was a fairly painless move and it was so exciting to scale
up our background workers and watch 20 slides a second get processed.
Now that Speaker Deck is on Heroku and S3 we have one less constraint
holding us back from releasing new features and hopefully leaving beta
soon.
