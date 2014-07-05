---
title: "'Changing Default Leiningen Version'"
created_at: Sun 06 Jul 2014 00:10:12 MSK
twitter: michaelklishin
layout: post
permalink: 2014-07-06-changing-default-leiningen-version
---

A little bit of Travis history trivia: Clojure was the 3rd language supported on Travis CI
(added in the fall of 2011). It was supported months before Java, in large part
because of how standardized the build system and testing conventions are in the
Clojure community.

## Breaking Changes is a Matter of When

As with every young ecosystem, at some point the crucial Clojure tool, [Leiningen](http://leiningen.org),
had to introduce a breaking version, 2.0. Project started switching to
Leiningen 2.0 long before it was GA, so we had to support 2 versions
on Travis: Leiningen 1 and Leiningen 2.

To do this, we provision two versions as `lein1` and `lein2` and let the user
specify what Leiningen version they need in `.travis.yml`. This has worked
for over 2 years now but Leiningen 1.x. isn't getting any updates.
Leiningen 2 is at `2.4.x` these days, and virtually every project out there
has switched to `2.x.` since 2012.

As a result, it makes little sense to keep Leiningen 1 the default. In the next
few weeks you'll see `lein` switch to point to Leiningen 2 in the Travis CI
environment. We will then get rid of Leiningen 1.x support entirely a few
months after that.


## How to Adapt to the Change

If your project already uses Leiningen 2.x, you'll be able to simply remove
the `lein: "lein2"` line from your `.travis.yml`. If you still use 1.x,
you'll have to add `lein: "lein1"`.


So long, Leiningen 1.x. You've served the Clojure community well for a few years
but maintaining you means at some point we *will* have to set our hair on fire!
