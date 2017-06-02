---
layout: post
category: posts
title: Garmin is the new Pebble
excerpt: I found a replacement for Pebble Time and you won't believe what it is
tags: [pebble, garmin, time, forerunner, fenix, apple, watch, smartwatch, running]
comments: true
---

I backed _Pebble Time_ on Kickstarter back in February 2015. I was very skeptical but people loved the original Pebble so I decided to give this one a try. I have worn it **every single day** since receiving it in June 2015 and I [loved that thing](/posts/2015/06/16/pebble-time-ismoothrun-ftw/). I was super excited when Pebble announced the Time 2. It would fix the only 2 pain points I had with Time - small screen and a lack of a heart rate monitor. I backed it without hesitation. But, as you know, all that **went tits up** when [Fitbit acquired Pebble](https://blog.getpebble.com/2016/12/07/fitbit/). :sob:

So ever since then I was stuck with my original Pebble Time which I still loved. But it was all scratched and the strap showed significant wear and tear. I[^1] was always on the lookout for the _next Pebble_. But there was no real smart watch alternative on the horizon. :disappointed:

Apple Watch has a display that turns on only when you flick your wrist[^2]. I mean, c'mon. How can you even remotely call that a _watch_ when the screen is turned off most of the time? And less than 1 day of battery life? Absolute **joke**. Not to even mention the touch screen interface. People sweat[^3], you know? :sweat_smile:

Android Wear does look nice. On the photos. In reality it's a very different story. The materials most manufacturers use are repulsive. Battery life is not great and they don't work that well with an iPhone.

Fitbit Blaze? :joy: Just look at it. Whoever decided to ship that disgusting piece of hardware was clearly blind. And even though they bought Pebble they have [no intentions](https://www.forbes.com/sites/paullamkin/2017/02/20/fitbit-has-zero-interest-in-building-a-pebble-smartwatch/) to build a _true_ smart watch.

<figure class="third">
  <img src="/images/posts/2017-05-16-apple-watch.jpg" title="Apple Watch">
  <img src="/images/posts/2017-05-16-lg-watch.jpg" title="LG Watch Sport">
  <img src="/images/posts/2017-05-16-fitbit-blaze.jpg" title="Fitbit Blaze">
  <figcaption>Apple Watch, LG Watch Sport, and Fitbit Blaze.</figcaption>
</figure>

A couple of weeks ago I saw the announcement of Garmin fēnix 5[^4]. It's a sport watch but it is _smart_. It has always-on display, 24/7 heart rate monitor, GPS and GLONASS, barometer, Wi-Fi, Bluetooth, ANT+, compass, thermometer, accelerometer, gyroscope,…, it has **everything**. The LCD has a pretty good resolution[^5] and the technology seems similar to that in Pebble Time. It has remarkable outdoor visibility. It even supports 3rd party watch faces, widgets, and apps that are available on their [Connect IQ App Store](https://apps.garmin.com/en-US/). You'd think that all this would mean a shitty battery life, right? Nope - **up to 2 weeks**. _What is this sorcery_? It has a downside though - price. **699,99€**[^6] is a significant amount of money. Also at **87g** it's more than _double_ the weight of Pebble Time[^7]. So I wasn't convinced.

But then - out of nowhere I see DC Rainmaker's[^8] [Forerunner 935 In-Depth Review](https://www.dcrainmaker.com/2017/03/garmin-forerunner-935-depth-review.html).

>So what’s the FR935 all about? Well in a nutshell it’s a cheaper version of the Fenix 5, with a plastic shell as opposed to metal. Basically – it could be named the Fenix 5P – for Plastic

It's **150€** less and at **49g** almost _half_ the weight. Same battery life. Same vast feature set. Could this be my ideal smart[^9] watch? As soon as it was [available in Slovenia](http://agp.si/garmin-forerunner-935-crna.html) I had to get it to test it out. And let me tell you - **I love it**!

<figure class="third">
  <img src="/images/posts/2017-05-16-fenix-5s.jpg" title="Fenix 5S">
  <img src="/images/posts/2017-05-16-fenix-5.jpg" title="Fenix 5">
  <img src="/images/posts/2017-05-16-forerunner-935.jpg" title="Forerunner 935">
  <figcaption>fēnix 5S, fēnix 5, and Forerunner 935 aka fēnix 5P.</figcaption>
</figure>

Being a software developer myself, I naturally wanted to write something for my new watch. I decided to try and port over one of my favorite iOS applications - [Weather Line](http://weatherlineapp.com/). It was not as simple as I'd imagined. I needed to learn the basics of a completely new language called [Monkey C](https://developer.garmin.com/connect-iq/programmers-guide/monkey-c/) :see_no_evil:. It's this weird JavaScript-ish system language that wants you to think that it's high level. You shouldn't treat it as such since you're developing for a device with very limited amount of memory and CPU. I also had to grasp how to find anything in their [API docs](https://developer.garmin.com/connect-iq/api-docs/). They're not bad at all, but they do lack examples. The best thing I had were a couple of sample apps that they include in the SDK.

After much copy/pasting, hacking, and cursing over the weekend I finally made something that worked the way I wanted it to. I submitted it to their app store and on Monday evening it got accepted. :tada:

<figure>
  <a href="https://apps.garmin.com/en-US/apps/6b9d2d26-d746-4377-830e-83422e3df45b">
    <img src="/images/posts/2017-05-16-forecast-line.gif" title="Forecast Line">
  </a>
</figure>

It's called [Forecast Line](https://apps.garmin.com/en-US/apps/6b9d2d26-d746-4377-830e-83422e3df45b#0) and it's a widget that shows 9 hour forecast with temperature trend line. It has individual semi-hourly icons to show the exact condition and temperature. Line turns blue if there's precipitation (rain, snow,…) and orange if there is none. Current conditions are always shown in the bottom center. It supports Celsius or Fahrenheit and 12 or 24 hour layout. For the data I chose [Dark Sky](https://darksky.net/) that uses 19 different weather sources and machine learning algorithms to get the best predictions out there.

At the time of writing it's out for just under 2 days and it already has over 400 downloads and 3 5-star reviews. I even got a user asking me for my PayPal so they can make a donation. And I got an email with this:

>I'm so happy someone has started developing for Garmin who actually cares about design.

I couldn't have been happier. :blush:

[^1]: and every other Pebble fan
[^2]: If you're lucky and it registers your intention. Lots of trial and error. Horrible UX.
[^3]: Or is it just me?
[^4]: What's the deal with this `ē`? No clue.
[^5]: 218x218px on the small model and 240x240px on the others
[^6]: Fenix 5 Sapphire - standard size model with Wi-Fi
[^7]: 42.5g
[^8]: This guy has the best reviews you totally should follow him!
[^9]: and sport
