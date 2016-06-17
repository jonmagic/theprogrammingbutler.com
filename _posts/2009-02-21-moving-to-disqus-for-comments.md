---
layout: post
title: Moving to Disqus for comments
---

I’ve been thinking about using Disqus for awhile now and finally decided
to bite the bullet when I realized I just couldn’t get the features I
wanted out of Mephisto’s built in comment system.

Setting [Disqus](http://disqus.com) up on your blog is easy enough,
they’ve got automated stuff for the popular hosted blogging platforms,
and easy to insert html/js for those of us running our own custom
blogging systems, like [Mephisto](http://mephistoblog.com).

If you are interested in doing this yourself, read on!

I wanted to be able to keep the 90+ comments I had already though, and
importing didn’t look like it was going to be easy. But then I found
[Michael Ivy’s post on importing from Mephisto to
Disqus](http://gweezlebur.com/2009/01/05/mephisto-to-disqus.html) and
got excited at how easy it looked to be. At first I tried using his
vanilla script, just filling in the blanks, but quickly realized there
were some problems:

1.  The script didn’t account for your mysql db having a password
2.  It gets the article url’s from the article rss feed, which only
    returns the last 15 articles by default

I started tackling the first problem by just changing one line in the
script to look like this:

> db = Sequel.mysql(db, :user =&gt; db\_user, :password =&gt; db\_pass,
> :host =&gt; ‘localhost’)

and then adding `db_pass = 'password_here'` to the options stuff above.
This kind of worked, except that one of the last lines in the script

> puts “Success: \#{comment.author} on \#{comment.title}”

errored out on comment.author, because Sequel isn’t taking into account
relationships between models in Mephisto.

At this point I decided to rework it a little and just use
./script/runner to run the export script, so that I could take full
advantage of the Rails app relationships. [Here is my updated
script](http://gist.github.com/68198).

Things still weren’t quite right though, I either had to modify Mephisto
to get back all my articles from the rss feed, or just use ActiveRecord
to pull all that stuff. I decided to edit
app/controllers/feed\_controller.rb and remove the `:limit =&gt; 15`
lines from the three methods at the bottom of that controller. I put
them back afterwards :-)

That should be it, worked great for me, putting all my existing comments
into Disqus. Then I just had to modify \_comments.liquid,
\_entry.liquid, and layout.liquid using the built in template editor in
Mephisto.

…nuf said
