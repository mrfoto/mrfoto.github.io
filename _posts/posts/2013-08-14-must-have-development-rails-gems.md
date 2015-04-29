---
layout: post
category: posts
title: Must Have Development Rails Gems
excerpt: Can't even develop straight without this pearls.
tags: [ruby, rails, gems]
comments: true
---

#TL;DR

[better_errors](https://github.com/charliesome/better_errors), [jazz_hands](https://github.com/nixme/jazz_hands), [bullet](https://github.com/flyerhzm/bullet), [quiet_assets](https://github.com/evrone/quiet_assets), [rack-mini-profiler](https://github.com/SamSaffron/MiniProfiler/tree/master/Ruby), [terminal-notifier-guard](https://github.com/Springest/terminal-notifier-guard), [figaro](https://github.com/laserlemon/figaro)

#About me

First things first - I'm a Rails newbie. I've been messing with it for about 6 months and I've been to this years RailsConf as a scholarship recipient. I've written a couple of Rails apps and I'm just diving into TDD and BDD since I've never done tests before.

#The gems

##[better_errors](https://github.com/charliesome/better_errors)
Seriously can't develop without this one anymore. It replaces the standard Rails error page with a much better and more useful error page. You should also install [binding\_of\_caller](https://github.com/banister/binding\_of\_caller) which gives you REPL and local/instance variable inspection which is just awesome. You can also use it with Pry, just put this in your development.rb initializer:

```ruby
BetterErrors.use_pry!
AwesomePrint.defaults = { plain: true }
```

##[jazz_hands](https://github.com/nixme/jazz_hands)
Now this is a collection gem - it includes many many many sweet gems:

* [Pry](http://pry.github.com) for a powerful shell alternative to IRB.
* [Awesome Print](https://github.com/michaeldv/awesome_print) for stylish pretty print.
* [Hirb](https://github.com/cldwalker/hirb) for tabular collection output.
* [Pry Rails](https://github.com/rweng/pry-rails) for additional commands (`show-routes`,
  `show-models`, `show-middleware`) in the Rails console.
* [Pry Doc](https://github.com/pry/pry-doc) to browse Ruby source, including C, directly from the
  console.
* [Pry Git](https://github.com/pry/pry-git) to teach the console about git. Diffs, blames, and
  commits on methods and classes, not just files.
* [Pry Remote](https://github.com/Mon-Ouie/pry-remote) to connect remotely to a Pry console.
* [Pry Debugger](https://github.com/nixme/pry-debugger) to turn the console into a simple debugger.
* [Pry Stack Explorer](https://github.com/pry/pry-stack_explorer) to navigate the call stack and
  frames.
* [Coolline](https://github.com/Mon-Ouie/coolline) and [Coderay](https://github.com/rubychan/coderay) for syntax highlighting as
  you type.

##[bullet](https://github.com/flyerhzm/bullet)
Now this is a very simple gem, that looks at your queries. Whenever you do a N+1 it'll log it and optionally alert you. There are many ways it can report to you, just read the README.

##[quiet_assets](https://github.com/evrone/quiet_assets)
Nothing more annoying that those assets requests spam messages in Rails log. This shuts it off.

##[rack-mini-profiler](https://github.com/SamSaffron/MiniProfiler/tree/master/Ruby)
It's a middleware that displays speed badge for every page. It shows a nice sidebar with all the DB requests and timings and such. Useful for identifying bottlenecks.

##[terminal-notifier-guard](https://github.com/Springest/terminal-notifier-guard)
Adds native notifications to Guard. Only useful if you use Guard and are on Mac OS 10.8+

##[figaro](https://github.com/laserlemon/figaro)
It's the best Rails configuration gem I came across. It provides a clean and simple way to configure your app and keep the private stuff private. This way you can easily open source projects without worrying about secret tokens and such. The best of all? It knows how to export those ENV vars to Heroku.

#Got more?

Do comment :)
