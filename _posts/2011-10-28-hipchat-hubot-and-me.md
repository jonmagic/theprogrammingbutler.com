---
layout: post
title: HipChat, hubot, and Me
---

How you can give Siri her very own robot brother with some help from
Heroku and HipChat.

Github released [hubot](https://github.com/github/hubot) this week and
geeks the world over have been transfixed by his awesomeness. He’s the
second robot butler to enter my life lately,
[Siri](http://www.apple.com/iphone/features/siri.html) being the first.
Together these two fulfill my every wish (not quite) and are at my beck
and call day and night (too true).

**<span class="caps">UPDATE</span>: for a slightly different take [try
these instructions by
@martinciu](http://martinciu.com/2011/11/deploying-hubot-to-heroku-like-a-boss.html)**

**<span class="caps">NOTE</span>: to learn more about writing hubot
scripts [read
this](http://jonmagic.com/blog/archives/2011/10/28/hubot-scripts-explained/)**

### Getting Started

The first step is to head on over to the [hubot
downloads](https://github.com/github/hubot/downloads) to grab yourself a
copy of the latest hubot tarball. Download it and then open your command
line to your download folder. It looked something like this for me:

```bash
cd Downloads
tar zxvf hubot-1.1.3.tar.gz
cd hubot
```

Make sure you have node.js and npm installed. I used
[homebrew](http://mxcl.github.com/homebrew/) to accomplish this.

```bash
brew install node
brew install npm
```

Then you can just run the hubot binary and it should install all the
necessary packages and fire right up.

```bash
bin/hubot
```

If you run into any issues at this point please consult the [hubot
Issues](https://github.com/github/hubot/issues) page on Github, because
someone has probably already run into the issue.

### Configuring Heroku and HipChat

First we need to initialize git for our hubot so he’s actually stored in
version control.

```bash
git init .
git add .
git commit -m "spawning my first robot!"
```

Next we create a new instance on the [Heroku cedar
stack](http://devcenter.heroku.com/articles/cedar) (assuming you already
are [setup to use
Heroku](http://devcenter.heroku.com/articles/quickstart)).

```bash
heroku create my_hubot_app_name --stack cedar
```

Then we need to setup hubot and Heroku to connect to our
[HipChat](http://hipchat.com) account.

This requires creating the user in HipChat and then going to your
account page in HipChat (https://mycompanyhere.hipchat.com/account/xmpp)
to get some values that we’ll need for configuring Heroku.

You’ll also need to go to the Group Admin in HipChat and the <span
class="caps">API</span> tab to create an <span class="caps">API</span>
Auth Token. Run the following commands replacing the values with the
ones that match in the HipChat settings:

```bash
heroku config:add HUBOT_HIPCHAT_JID=<Username>

heroku config:add HUBOT_HIPCHAT_NAME=<Room nickname>
# example: heroku config:add HUBOT_HIPCHAT_NAME="Geoffrey Butler"

heroku config:add HUBOT_HIPCHAT_PASSWORD=<Password you created for hubots user>
heroku config:add HUBOT_HIPCHAT_TOKEN=<Token from Group Admin and API>
```

We also need to add the RedisToGo addon. (Thanks to [Graham
Siener](http://profitably.com/) for pointing this out)

```bash
heroku addons:add redistogo:nano
```

Now that Heroku is configured we need to slightly modify our Procfile to
use the right adapter and name. Mine looks like this:

```bash
app: bin/hubot -a hipchat -n "Geoffrey Butler"
```

Replace Geoffrey Butler with whatever you named the user in HipChat.
This should exactly match the Room nickname we set above. Once you’ve
updated the Procfile and saved it we need to commit it with git.

```bash
git add Procfile
git commit -m "updated Procfile to use hipchat adapter and hipchat room nickname"
```

### Deploying to Heroku

Now we should be ready to deploy.

```
git push heroku master
```

This step failed for me at first. I had to edit package.json and change
the dependencies section to look like this:

```json
"dependencies": {
  "hubot": "1.1.0",
  "hubot-scripts": "1.1.0",
  "optparse": "1.0.1"
}
```

The latest version of hubot-scripts blows up on the Heroku Cedar stack
unfortunately. So after this step I committed my changes one more time
and deployed.

```bash
git add package.json
git commit -m "changed dependencies"
git push heroku master
```

Woot! It worked! Now that its deployed we just need to start it up.

```bash
heroku ps:scale app=1
```

Inside our HipChat rooms Geoffrey suddenly appeared and I was able to
talk to him.

```
@geoffrey help
(thanks|thank you) - say thanks to your butler
<keyword> tweet - Returns a link to a tweet about <keyword>
<user> is a badass guitarist - assign a role to a user
<user> is not a badass guitarist - remove a role from a user
animate me <query>  - The same thing as `image me`, except adds a few
ascii me <text> - Show text in ascii art.
check domain <domainname> - returns whether a domain is available
convert me <expression> to <units> - Convert expression to given units.
gem whois <gemname> - returns gem details if it exists
haters - Returns a random haters gonna hate url
help - Displays all of the help commands that Hubot knows about.
image me <query>    - The Original. Queries Google Images for <query> and
map me <query> - Returns a map view of the area returned by `query`.
math me <expression> - Calculate the given expression.
mustache me <query> - Searches Google Images for the specified query and
mustache me <url>   - Adds a mustache to the specified URL.
remind me in <time> to <action>    - Set a reminder in <time> to do an <action>
ship it - Display a motivation squirrel
show storage - Display the contents that are persisted in redis
show users - Display all users that hubot knows about
translate me <phrase> - Searches for a translation for the <phrase> and then
translate me from <source> into <target> <phrase> - Translates <phrase> from <source> into <target>. Both <source> and <target> are optional
who is <user> - see what roles a user has
youtube me <query> - Searches YouTube for the query and returns the video
```

Awesome! Enjoy :)
