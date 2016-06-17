---
layout: post
title: Twelve (gauge)
---

Today I hacked together an easy to use gem for accessing the
[Gauges](http://get.gaug.es) API.

When I started this morning 12-gauge was the first thing I thought, so I
called the gem Twelve (silly I know).

I had fun figuring out the <span class="caps">API</span> (with a little
help from [Brandon](http://twitter.com/bkeepers)) and then writing the
gem using some of the proxy object and method missing stuff I was
learning a few weeks ago.

### Installation

```bash
gem install twelve
```

### Usage

Get the client ready:

```ruby
access_token = "abcd1234"
bfg = Twelve.new(access_token)
```

Request your Gauges info:

```ruby
bfg.me
```

For me I got this back:

```json
{"name"=>"Jonathan Hoyt", "urls"=>{"self"=>"https://secure.gaug.es/me", "gauges"=>"https://secure.gaug.es/gauges", "clients"=>"https://secure.gaug.es/clients"}, "id"=>"...", "last_name"=>"Hoyt", "first_name"=>"Jonathan", "email"=>"jonmagic@gmail.com"}
```

Next try these:

```ruby
bfg.clients
bfg.gauges
```

### More Documentation and Examples

Its a full-fledged client, so you can create, update, and delete gauges
as well as see all the different types of information available on a
gauge. See the docs on [GitHub](https://github.com/jonmagic/twelve)!
