---
layout: post
title: New Team and Lessons Learned
---

The past few months I have been building a new team at
[GitHub](https://github.com) focused on solving problems for our
business teams. Here are a few valuable lessons we learned along the
way.

### Solving the right problem

We solve problems for a living and we have one major constraint, our
time. This means we need to be thoughtful in choosing which problems to
solve. We cannot solve them all.

We decided to solve employee expenses at GitHub by building our own
expensing system. We had evaluated [3rd party
services](http://expensify.com) and while they did 90% of what we
needed, that last 10% made it seem like it was worth doing on our own.

What we failed to account for were the other opportunities, the other
problems that needed solved, that ultimately would have a more lasting
impact on GitHub.

If we use our company vision, to help people [build software better
together](https://github.com/home), as a framework for deciding what to
work on, choosing the right problem to solve becomes much easier.

We should be sensitive to [opportunity
costs](http://en.wikipedia.org/wiki/Opportunity_cost). Solve the problem
that will have the greatest impact with the lowest cost.

### Failing fast

After choosing the wrong problem to solve we did not set clear goals so
that we knew what success or failure meant. As a result it took us four
months to realize we were working on the wrong thing.

Our first goal was to ship a system that received receipts, connected
them to transactions, provided automatic and manual classification, and
then entered the data into our accounting system.

The more I learn about software development, or solving any problem
really, the more I realize a [winning
percentage](http://en.wikipedia.org/wiki/Winning_percentage) requires
breaking down problems (and their solutions) into smaller and smaller
pieces. Shipping quickly and constant iteration mean faster course
corrections and less costly failures.

The fact that we could not easily break the expensing problem down into
smaller pieces should have been a red flag.

We can reduce the costs of failure, both emotionally and economically,
if we fail fast. We can’t fail fast unless we ship quickly and iterate.

### Do the simplest thing first

We also started building a platform for different teams (and apps) at
GitHub to be able to easily invoice customers. We dreamt up the perfect
platform for invoicing, without having tried the simplest thing first.

The lie we often believe is that we understand what our constraints will
be in a week, or a month, or six months and therefore we can save time
by optimizing early. The truth is that we cannot foresee the future.

In the end we learned that invoicing integration needed to be built
inside of the products it serves first. After it has been proven it can
possibly be extracted into a shared service. This sounds like more work
in the long run, but ultimately this process can adapt to change more
quickly and easily.

### One more thing

We could have avoided a lot of heartache and wasted resources if I had
sought mentorship from people with more experience and context at
GitHub.

For long term success I need to constantly be learning, which means
keeping an open mind and a humble spirit. I look forward to the journey
\\m/
