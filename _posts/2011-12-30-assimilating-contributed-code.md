---
layout: post
title: Assimilating Contributed Code
---

This year I authored several RubyGems and just this week finally learned
how to work with a contributor.

**<span class="caps">UPDATE</span>:**
[@bryckbost](http://twitter.com/bryckbost) points out that the
[github-gem](https://github.com/defunkt/github-gem) does exactly what I
wanted to do. See the **Fetching and Evaluating Downstream Changes**
section of the <span class="caps">README</span>.

Of course [GitHub](http://github.com) has the great **Merge pull
request** option when an auto-merge is possible, and I use that quite
often, but the workflow on <span class="caps">OSS</span> projects
sometimes requires you to run the tests locally and make any
modifications before merging it.

A quick search didn’t turn up any easy to read instructions, and I’m no
git guru, so it took me a few minutes to figure out a simple workflow.

Here is how I checked out, tested, modified, and merged a [massive pull
request](https://github.com/jonmagic/ghee/pull/1) for
[Ghee](http://github.com/jonmagic/ghee) from [Ryan
Rauh](https://github.com/rauhryan) this week.

### 1. Clone my repo and create a feature branch

```bash
git clone git@github.com:jonmagic/ghee.git
cd ghee
git checkout -b repos_support master
```

This creates a new branch called repos\_support, based off of master,
and checks it out.

### 2. Pull contributors code into your local branch

```bash
git pull https://github.com/rauhryan/ghee.git repos_support
```

This pulls the repos\_support branch from the remote repo and merges it
into the branch you have checked out (which we also called
repos\_support).

### 3. Run tests, make modifications, commit changes

```bash
bundle exec rake
touch OHNOES.txt
git add OHNOES.txt
git commit -m "Added OHNOES"
```

### 4. Checkout master, merge feature branch, push

```bash
git checkout master
git merge repos_support
git push
```

### Conclusion

This workflow follows the [kiss
principle](http://en.wikipedia.org/wiki/KISS_principle), so it worked
quite well for me.

**Please give me feedback**. I would love to hear about how other people
accomplish this task, so I encourage you to leave links/tips/tricks in
the comments below.

Also be sure to checkout [Ryan’s awesome
work](https://github.com/jonmagic/ghee/compare/71fe16a34aad6edf9d17379e7f3dd413e6855e21...2065149ff01be1770d3d51bdb8b9272ebb972e4d)
on [Ghee](http://github.com/jonmagic/ghee), a simple ruby client for the
[GitHub <span class="caps">API</span>
V3](http://developer.github.com/v3/).
