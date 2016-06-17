---
layout: post
title: hubot Scripts Explained
---

Ok, so now you've got your shiny new hubot up and ready to listen to
your every command. But what should we tell him to do with our nonsense!

### Basics

Scripts for [hubot](https://github.com/github/hubot) are written with
[CoffeeScript](http://jashkenas.github.com/coffee-script/). This is what
a basic script looks like:

```coffeescript
# hubot greeting.
#
# (hi|hello) - say hi to your butler

module.exports = (robot) ->
  robot.respond /hi|hello/i, (msg) ->
    msg.send "Howdy!"
```

Lets break this script down. The first line is just a description of the
script. The third line tells hubot what to include in the help (when you
ask hubot for help).

The actual code starts on the module.exports line. Every script you make
will start with that line.

```coffeescript
module.exports = (robot) ->
```

The next line tells hubot to respond to hi and hello.

```coffeescript
robot.respond /hi|hello/i, (msg) ->
```

It uses a [regular
expression](http://en.wikipedia.org/wiki/Regular_expression) to parse
the text, looking for the words hi and hello. The i after the last slash
tells the regular expression to not be case sensitive, so it will also
match Hi and Hello.

I like to use [rubular](http://rubular.com/) for writing and testing
regular expressions. Its quick, easy to use, and while javascript
regular expressions aren’t exactly like ruby regular expressions I
haven’t run into any inconsistencies yet.

Finally we tell hubot to take the message and send a message back.

```coffeescript
msg.send "Howdy!"
```

### Respond vs Hear

I didn’t discover this at first and thought that hubot only responded to
commands directed at him, but then I discovered robot.hear! Whereas
robot.respond only matches messages directed at hubot, robot.hear will
run your regular expression against any chat message!

```coffeescript
# Hubot has an attitude

module.exports = (robot) ->
  robot.hear /tired|too hard|to hard|upset|bored/i, (msg) ->
    msg.send "Panzy"
```

See what I did there :) Any time someone in our chat room says they are
tired, that something is too hard, upset, or bored, hubot tells them
they’re a panzy. Oh yeah. This robot butler has an attitude.

### Random

I saw this used first in the shipit script, which displays a random
shipit squirrel for your viewing pleasure whenever someone says the
words “ship it” in your chat room.

```coffeescript
# Rodent Motivation
#
# ship it - Display a motivation squirrel
#

squirrels = [
  "http://img.skitch.com/20100714-d6q52xajfh4cimxr3888yb77ru.jpg",
  "https://img.skitch.com/20111026-r2wsngtu4jftwxmsytdke6arwd.png",
  "http://cl.ly/1i0s1r3t2s2G3P1N3t3M/Screen_Shot_2011-10-27_at_9.36.45_AM.png",
  "http://shipitsquirrel.github.com/images/squirrel.png"
]

module.exports = (robot) ->
  robot.hear /ship it/i, (msg) ->
    msg.send msg.random squirrels
```

Notice the array that we create with 4 different shipit squirrel images.
Then notice this line:

```coffeescript
msg.send msg.random squirrels
```

The msg object has a random method on it which we can pass an array and
it will pick a random item from that array! Super handy to keep things
from getting repetitive.

### Reply

You can reply to a user by changing the send command to reply like this:

```coffeescript
msg.reply "Why thank you sir!"
```

Replies will be directed at a specific user, example: “@hoyt Why thank
you sir!”

### Http

So far we’ve only talked about how to make hubot listen and respond in
various ways. Hubot really starts to get interesting when we empower him
to go out and do our bidding in the larger world though. This is where
hubot really starts to become powerful!

```coffeescript
# Whois for gems, because gem names are like domains in the 90's
#
# gem whois <gemname> - returns gem details if it exists
#

module.exports = (robot) ->
  robot.respond /gem whois (.*)/i, (msg) ->
    gemname = escape(msg.match[1])
    msg.http("http://rubygems.org/api/v1/gems/#{gemname}.json")
      .get() (err, res, body) ->
        try
          json = JSON.parse(body)
          msg.send "   gem name: #{json.name}\n
     owners: #{json.authors}\n
       info: #{json.info}\n
    version: #{json.version}\n
  downloads: #{json.downloads}\n"
        catch error
          msg.send "Gem not found. It will be mine. Oh yes. It will be mine. *sinister laugh*"
```

This script is doing quite a bit so we’ll dissect it line by line.

```coffeescript
robot.respond /gem whois (.*)/i, (msg) ->
```

This tells hubot to look for messages directed at him that have the
words “gem whois” and then some string.

```coffeescript
gemname = escape(msg.match[1])
```

Now I grab the gemname from the regular expression. msg.match with an
integer will match the captured item from the regular expression. You
use parenthesis to capture strings in regular expressions, and they get
numbered left to right by however many there are. In this case its the
first one, so we pass 1 to msg.match and then assign it off to our
variable gemname.

```coffeescript
msg.http("http://rubygems.org/api/v1/gems/#{gemname}.json")
```

Next we tell the msg.http object to use this url, with the gemname
interpolated in it.

```coffeescript
.get() (err, res, body) ->
```

The .get() function kicks off the request and returns 3 objects, err,
res, and body. In this case we’re only interested in body.

```coffeescript
try
  json = JSON.parse(body)
  msg.send "   gem name: #{json.name}\n
    owners: #{json.authors}\n
    info: #{json.info}\n
    version: #{json.version}\n
    downloads: #{json.downloads}\n"
catch error
  msg.send "Gem not found. It will be mine. Oh yes. It will be mine. *sinister laugh*"
```

If <span class="caps">JSON</span>.parse is able to parse the body then
it displays the gem information, if it errors we get the “Gem not found”
message.

### Advanced <span class="caps">HTTP</span>

What if you want to hit an <span class="caps">API</span> that requires
authentication? Here is a script that uses http basic auth when hitting
the [dnsimple](http://dnsimple.com) api to check domain name
availability.

```coffeescript
# Domain availability via DNSimple, requires you set
# DNSIMPLE_USERNAME & DNSIMPLE_PASSWORD environment variables
#
# check domain <domainname> - returns whether a domain is available
#

module.exports = (robot) ->
  robot.hear /check domain (.*)/i, (msg) ->
    domain = escape(msg.match[1])
    user = process.env.DNSIMPLE_USERNAME
    pass = process.env.DNSIMPLE_PASSWORD
    auth = 'Basic ' + new Buffer(user + ':' + pass).toString('base64');
    msg.http("https://dnsimple.com/domains/#{domain}/check")
      .headers(Authorization: auth, Accept: 'application/json')
      .get() (err, res, body) ->
        switch res.statusCode
          when 200
            msg.send "Sorry, #{domain} is not available."
          when 404
            msg.send "Cybersquat that s***!"
          when 401
            msg.send "You need to authenticate by setting the DNSIMPLE_USERNAME & DNSIMPLE_PASSWORD environment variables"
          else
            msg.send "Unable to process your request and we're not sure why :("
```

We do the same thing as the last example, grabbing the domain name that
is captured by the regular expression, but then things get a bit
different.

```coffeescript
user = process.env.DNSIMPLE_USERNAME
pass = process.env.DNSIMPLE_PASSWORD
```

Here we grab some environment variables and assign them to variables. If
you are [deploying hubot to
Heroku](http://jonmagic.com/blog/archives/2011/10/28/hipchat-hubot-and-me/)
then setting environment variables is crazy easy:

```coffeescript
heroku config:add DNSIMPLE_USERNAME=john@doe.com DNSIMPLE_PASSWORD=4w3s0m3p4ssw0rd
```

Next we have to create the auth string that we’ll stuff into the
authorization header.

```coffeescript
auth = 'Basic ' + new Buffer(user + ':' + pass).toString('base64');
```

Creating that auth string is some javascript voodoo that took me awhile
to figure out, finally finding an article on
[stackoverflow](http://stackoverflow.com/questions/3905126/how-to-use-http-client-in-node-js-if-there-are-basic-authorization)
that had the magic I needed.

```coffeescript
msg.http("https://dnsimple.com/domains/#{domain}/check")
  .headers(Authorization: auth, Accept: 'application/json')
  .get() (err, res, body) ->
```

The really interesting line in the code above is the .headers() line. We
can set headers for the http request before calling .get(), allowing us
to configure the Authorization and Accept headers! Now the last bit.

```coffeescript
switch res.statusCode
  when 200
    msg.send "Sorry, #{domain} is not available."
  when 404
    msg.send "Cybersquat that s***!"
  when 401
    msg.send "You need to authenticate by setting the DNSIMPLE_USERNAME & DNSIMPLE_PASSWORD environment variables"
  else
    msg.send "Unable to process your request and we're not sure why :("
```

The response (res) object has a statusCode method on it which we can use
to match http response codes. Based on the dnsimple api I was able to
make a simple switch statement with the correct replies for each status
code.

### Conclusion

I hope this is helpful to some folks out there. I can’t wait to see what
other hubot scripts people write!

Make sure to fork the
[hubot-scripts](https://github.com/github/hubot-scripts) repo, add your
scripts, and do a pull request once you’ve got them working. The gem
whois and dnsimple scripts above have already been accepted into the
hubot-scripts library!

Enjoy :)
