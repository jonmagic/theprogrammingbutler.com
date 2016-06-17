---
layout: post
title: Robots can do support too
---

GitHub launched the [Atom beta](http://atom.io) this week and the
response has been great. As the first day was winding down a coworker
suggested we write an FAQ and add a robot to answer the frequently asked
questions in the irc channel where people were congregating. Here's how
we taught [hubot](http://hubot.github.com) to do support.

### Questions and answers

First my coworker gathered the questions that were being asked over and
over again:

-   where do I get an invite?
-   is there a windows or linux version of atom?
-   how much will Atom cost?

Next he wrote short and to the point answers:

-   Are you looking for an atom invite? Go to https://atom.io/ and put
    in your email, or join the \#product-invitations room.
-   Are you looking for a windows or linux version of atom? We don’t
    have one yet, but we will in the future.
-   Were you inquiring in the channel about Atom’s price? We haven’t set
    a price yet, but expect it will be on par with the cost for
    similar editors.

Finally he compiled the regular expressions that we could use in hubot
to listen for people’s questions and then reply to them with the
answers.

```javascript
/invit(es?|ation)/i
/(windows|linux)/i
/(pric(e|ing)|cost)/i
```

### Training the robot

Meanwhile I used the [Getting
Started](https://github.com/github/hubot/blob/master/docs/README.md)
instructions to fire up a hubot instance.

Using [npm](http://shapeshed.com/setting-up-nodejs-and-npm-on-mac-osx/)
I installed the hubot and coffee-script packages.

```bash
npm install -g hubot coffee-script
```

Next I created the hubot instance.

```bash
hubot --create atomicHubot
cd atomicHubot
git init .
git add .
git commit -m "Create atomicHubot"
```

Then I started hacking on the script (this is the final iteration with
my work and my coworkers).

```coffeescript
# Description:
#   Replying to people in atom channels on freenode.
#

module.exports = (robot) ->

  isNotified = (keyword, username) ->
    robot.brain.data[keyword] ?= []
    robot.brain.data[keyword].some (x) -> username == x

  replyTo = (user, msg) ->
    robot.send({user: {name: user}}, msg)

  robot.hear /invit(es?|ation)/i, (msg) ->
    username = msg.message.user.name

    unless isNotified("invite", username)
      replyTo(username, "Are you looking for an atom invite?  Go to https://atom.io/ and put in your email, or join the #product-invitations room.")
      robot.brain.data.invite.push username

  robot.hear /(windows|linux)/i, (msg) ->
    username = msg.message.user.name

    unless isNotified("winux", username)
      replyTo(username, "Are you looking for a windows or linux version of atom?  We don't have one yet, but we will in the future.")
      robot.brain.data.winux.push username

  robot.hear /(pric(e|ing)|cost)/i, (msg) ->
    username = msg.message.user.name

    unless isNotified("price", username)
      replyTo(username, "Were you inquiring in the channel about Atom's price?  We haven't set a price yet, but expect it will be on par with the cost for similar editors.")
      robot.brain.data.price.push username
```

Every so often I would test the script in hubot’s shell console.

```
bin/hubot
> where can I get an invite?
hubot> jonmagic: Are you looking for an atom invite?  Go to https://atom.io/ and put in your email, or join the ##atom-invitations room.
```

Next I installed the [irc adapter](https://github.com/nandub/hubot-irc)
in atomicHubot.

```bash
npm install hubot-irc --save && npm install
git add .
git commit -m "Add irc adapter"
```

Now I needed atomicHubot to actually live on the internet and connect to
the irc channel so I read the [Deploying Hubot to
Heroku](https://github.com/github/hubot/blob/master/docs/deploying/heroku.md)
instructions. These required that I have the [Heroku
toolbelt](http://toolbelt.heroku.com) installed.

Step 1 was creating the application on Heroku and configuring it.

```bash
heroku create atomichubot
heroku addons:add redistogo:nano
heroku config:set HEROKU_URL=http://atomichubot.herokuapp.com
heroku config:set HUBOT_IRC_NICK=atomicHubot
heroku config:set HUBOT_IRC_ROOMS=#channel-name
heroku config:set HUBOT_IRC_SERVER=irc.freenode.net
heroku config:set HUBOT_IRC_UNFLOOD=true
```

Step 2 was deploying to Heroku.

```bash
git push heroku master
```

**That was it, I didn’t have to do any trouble shooting, atomicHubot
connected to the irc channel and began fielding questions!**

### Conclusion

Adding this hubot to the irc channel helped reduce the number of
questions we had to answer and increased the speed at which common
questions were answered.

There are probably easier ways to setup auto reply answers in irc
channels but hubot is a tool I’m familiar with and love to hack on. It
only took a few minutes to setup and I’ll probably use the same
technique in the future.

This may not work for everyone but hubot sure helped out in a pinch,
give it a try sometime. For tips on writing hubot scripts see my post
[hubot Scripts
Explained](http://theprogrammingbutler.com/blog/archives/2011/10/28/hubot-scripts-explained/).
