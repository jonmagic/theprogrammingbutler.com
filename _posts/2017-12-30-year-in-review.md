---
layout: post
title: Year in review
---

This year flew by with a couple life changing family events, several projects shipped at work, and a lot of learning.

![kite](https://cl.ly/0Q0J0o25082o/IMG_5507.jpg)

## Family

We took two family trips to Florida this year to visit Natalie's parents. The first trip was after her father found out he had cancer and the second trip was to help her mom pack up and move after he passed away. Of course these weren't easy trips but I cherish the time we had with them.

Adalyn is growing up faster than I can comprehend most days. She's opinionated, independent, and can be sweet and then harsh in the span of a few seconds. Right now I'm trying to learn how to help her concentrate on a task or project for more than a few seconds at a time.

In August Natalie and I celebrated our tenth wedding anniversary (and fifteenth year together). My mom flew in to take care of Adalyn so that Natalie and I could get away for a few days. We flew to Portland and had a great time exploring a new city kid free!

The final piece of big news is that Natalie is pregnant and due in April!

## Work

I can't go into detail about most of my projects now that I'm on the security team at [GitHub](https://github.com). I still write blog posts regularly but they only get posted to a private work blog. What I can talk about here is some of the cool tech I've been learning and using.

![team](https://cl.ly/0K0l2B0K2I36/IMG_4301.jpg)

### React, GraphQL, and design

One of my responsibilities is building workflow tools for a team of analysts. Most of these workflows are queues and the analysts have to review items in the queue as quickly as possible.

We chose [Rails](https://rubyonrails.org) with [webpacker](https://github.com/rails/webpacker) and a [React](https://reactjs.org/) frontend implemented in [Typescript](https://www.typescriptlang.org/) that reads from a [GraphQL](http://graphql.org/) API using the [Apollo client](https://www.apollographql.com/client/) library. We've been able to build super fast and information rich user interfaces with this tech stack and we're loving it for the most part.

One thing that hasn't worked great has been combining multiple API's into a single unified GraphQL API, specifically re-exposing the [GitHub Platform](https://developer.github.com/early-access/platform-roadmap/) in our apps GraphQL API. We've had to duplicate a lot of the objects the GitHub Platform exposes and whenever we want to expose a new object or field we have to touch half a dozen places in our codebase.

Thankfully the folks over at Apollo have built [a server side solution](https://dev-blog.apollodata.com/graphql-schema-stitching-8af23354ac37) but it's implemented in javascript so we're planning on swapping out Rails in our stack for a node app. We believe [schema stitching](https://www.apollographql.com/docs/graphql-tools/schema-stitching.html) will have a significant impact on our development speed and maintainability.

I've also spent a good deal of time reading about user interface design and applying that knowledge to the analyst workflows. I started by reading through [this site from 1999 by Jenifer Tidwell](http://www.mit.edu/~jtidwell/common_ground.html) and am now reading her book [Designing Interfaces: Patterns for Effective Interaction Design](http://designinginterfaces.com/).

### Machine learning

We've deployed multiple models to production now and have pipelines for training, testing, tuning, and deploying new models. While I haven't been very involved with the actual model building process I have been spending a lot of my time developing new features for us to use in our models.

During model development our ML stack is [Presto](https://prestodb.io/), [Jupyter](http://jupyter.org/), and [scikit-learn](http://scikit-learn.org/). When it's time to put things into production we use [Airflow](https://airflow.apache.org/) to train and tune models on a regular schedule and then the models are deployed as microservices in our [kubernetes](https://kubernetes.io/) cluster.

### Stream processing

Over the past few months we've switched to publishing our signals as [protobuf](https://developers.google.com/protocol-buffers/) messages to [kafka](https://kafka.apache.org/) so that we can use any number of consumers and start experimenting with stream processing.

We're currently running two types of stream processors. The first is a Ruby app using the [Racecar gem](https://github.com/zendesk/racecar). This app has let us experiment quickly with new streams and has helped us enable everyone on the team to do some basic stream processing.

The second one we've been experimenting with is [Flink](https://flink.apache.org/). It is way faster and has many more features than our simple ruby consumer app but we're still ironing out the development process for the rest of our team as you have to write Flink apps with Java, [Scala](https://www.scala-lang.org/), or [Kotlin](https://kotlinlang.org/). Our initial spike with Flink was in Scala but recently we've been writing apps with Kotlin which I think we'll end up preferring to Scala or Java.

## 2017 Reading List

* [A Man on the Moon: The Voyages of the Apollo Astronauts](https://www.audible.com/pd/A-Man-on-the-Moon-The-Voyages-of-the-Apollo-Astronauts-Part-1-Audiobook/B016J1NMR6)
* [Cyberspies: The Secret History of Surveillance, Hacking, and Digital Espionage](https://www.audible.com/pd/Cyberspies-Part-1-The-Secret-History-of-Surveillance-Hacking-and-Digital-Espionage-Audiobook/B01FV0BT8U)
* [Into the Black: The Extraordinary Untold Story of the First Flight of the Space Shuttle Columbia and the Astronauts Who Flew Her](https://www.audible.com/pd/Into-the-Black-Part-1-The-Extraordinary-Untold-Story-of-the-First-Flight-of-the-Space-Shuttle-Columbia-and-the-Astronauts-Who-Flew-Her-Audiobook/B01DUV8W32)
* [Hidden Figures: The American Dream and the Untold Story of the Black Women Mathematicians Who Helped Win the Space Race](https://www.audible.com/pd/Hidden-Figures-The-American-Dream-and-the-Untold-Story-of-the-Black-Women-Mathematicians-Who-Helped-Win-the-Space-Race-Audiobook/B01I28NTJU)
* [The Marvelous Pigness of Pigs: Respecting and Caring for All God's Creation](https://www.audible.com/pd/The-Marvelous-Pigness-of-Pigs-Respecting-and-Caring-for-All-Gods-Creation-Audiobook/B01D3MDWEW)
* [Apollo 8: The Thrilling Story of the First Mission to the Moon](https://www.audible.com/pd/Apollo-8-The-Thrilling-Story-of-the-First-Mission-to-the-Moon-Audiobook/B06Y5Q7YHS)
* [Radical Candor: Be a Kick-Ass Boss Without Losing Your Humanity](https://www.audible.com/pd/Radical-Candor-Be-a-Kick-Ass-Boss-Without-Losing-Your-Humanity-Audiobook/B01MZ6RMS4)
* [The Manager's Path: A Guide for Tech Leaders Navigating Growth and Change](https://www.amazon.com/Managers-Path-Leaders-Navigating-Growth/dp/1491973897/ref=sr_1_1?ie=UTF8&qid=1514616553&sr=8-1&keywords=managers+path)
* [Fullstack React](https://www.fullstackreact.com/)
* [The Complete Redux Book](https://leanpub.com/redux-book)
* [Rules of Machine Learning: Best Practices for ML](http://martin.zinkevich.org/rules_of_ml/rules_of_ml.pdf)
* [The Manga Guide to Linear Algebra](https://www.nostarch.com/linearalgebra)
* [Deep Learning](https://www.amazon.com/Deep-Learning-Adaptive-Computation-Machine/dp/0262035618/ref=pd_sim_14_4?_encoding=UTF8&pd_rd_i=0262035618&pd_rd_r=ZVE3307PRXX1DD691HQC&pd_rd_w=jeWjv&pd_rd_wg=Vn7CM&psc=1&refRID=ZVE3307PRXX1DD691HQC)
* [Introduction to Apache Flink: Stream Processing for Real Time and Beyond](https://www.amazon.com/Introduction-Apache-Flink-Stream-Processing/dp/1491976586)
* [Learning Apache Flink](https://www.amazon.com/Learning-Apache-Flink-Tanmay-Deshpande/dp/1786466228/ref=pd_lpo_sbs_14_img_0?_encoding=UTF8&psc=1&refRID=7HN2DZ597H9V24ZYE8A7)
* [Stream Processing with Apache Flink](https://www.safaribooksonline.com/library/view/stream-processing-with/9781491974285/)
* [Kafka: The Definitive Guide](https://www.safaribooksonline.com/library/view/kafka-the-definitive/9781491936153/)
* [Mastering Redis](https://www.safaribooksonline.com/library/view/mastering-redis/9781783988181/)
* [The Tao of Microservices](https://www.safaribooksonline.com/library/view/the-tao-of/9781617293146/)

## Stop, Start, Continue for 2018

I need to stop hurting my health with snacks and sugary drinks and stop working late nights and being immobile for hours on end staring at my laptop.

I would like to start exercising consistently, finding medical help for ongoing pain, spending more time playing with Adalyn and hanging out with Natalie, and interviewing again.

I'm going to continue studying machine learning and learning new technologies while consistently shipping at work, supporting my family and my teammates, and taking time to reflect and evolve.

## Thank you!

Thank you to everyone who helped me through 2017, especially Natalie and Adalyn, my parents, and my teammates at GitHub :heart:

![adalyn birthday](https://cl.ly/0614260n3i2z/IMG_4359.jpg)
