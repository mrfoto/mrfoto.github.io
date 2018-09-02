---
layout: post
category: posts
title: Journaling
excerpt: In order to further practice stoic philosophy I started journaling with Day One and Workflow.
tags: [stoic, philosophy, stoicism, journal, journaling, day one, workflow, ios, goodreads, ruby]
comments: true
---

About half a year ago my life changed _somewhat drastically_. I've read [A Guide to the Good Life: The Ancient Art of Stoic Joy](https://www.amazon.com/o/ASIN/1522632735/parpaspod-20). The book changed **something inside me**, and for the first time I felt like I needed a _life philosophy_. I've been practicing many of the [stoic exercises](https://dailystoic.com/what-is-stoicism-a-definition-3-stoic-exercises-to-get-you-started/) without even knowing it. All the others made sense on paper so I saw no reason not to practice more of them.

I'm trying ever since to be more in line with the philosophy and the results are noticeable. I'm more relaxed, have more energy, worry less, it's almost impossible to get me to lose my temper,…. But most important: I actually feel happy about my life and where I'm at.

One of the exercises all ancient stoics seemed to practice is [journaling](https://dailystoic.com/stoic-art-of-journaling/). I never had a journal and it seemed to me as something you do in your teenage years. But I have heard many people rave about journaling and how it makes their lives better. And more or less all of them say they do it in either **physical form** or in [**Day One**](http://dayoneapp.com/). My handwriting is so bad I can barely read my own scribbles so for me the answer was clear: if I'm going to do it, it's going to be with a keyboard.

About a week ago, [Day One released a major new version](http://dayoneapp.com/2018/08/version-3/). This was just the push I needed to get started. I downloaded it, opened it, and was faced with a **huge white wall**. What do I do now? There are no predefined templates. There are no guides to ease you into the practice. Not even a sample page of what you can do. Huh, now what? I can't freeform write, I need structure.

I went googling and I found the exact thing: [Five Minute Journal](https://www.intelligentchange.com/products/the-five-minute-journal). It's based on a very simple but scientifically confirmed notion:

>The Five Minute Journal is your secret weapon to focus on the good in your life, become more mindful, and live with intention. With a simple structured format based on positive psychology research, you will start and end each day with gratitude. Thousands who use the journal have seen increased happiness, better relationships, and have become more optimistic.

You take 5 minutes in the morning to start your day on a positive note and set intention to make your day great. You take another 5 minutes before bedtime where you reflect on the good throughout your day, ensuring you end your day on a positive note.

<figure>
  <img src="/images/posts/2018-09-02/5_minute_journal.jpeg" title="Five Minute Journal">
</figure>

Now all I had to do is change the very well designed physical journal into a Day One template. One problem though - Day One doesn't support templates[^1]. This seems very weird to me, since I would consider it a basic functionality of a journaling app, not a feature that is still missing in v3. But luckily they do have a [Workflow](https://workflow.is/) action, and you can do all you want with it.

I made a nicely formatted **Morning Routine** and **Evening Routine**, but it was missing one more thing. The physical 5 minute journal has a nice quote to start every day and I wanted that as well. Since I'm interested in what stoic philosophers have to say, I of course wanted their quotes. I didn't find any service that would provide an API with a random stoic quote so it meant I had to make it myself.

There are many websites with quotes but few as maintained as [Goodreads](https://www.goodreads.com/). I made a [simple and stupid Ruby script](https://gist.github.com/mrfoto/31420d5ecc7373bf0f58ec23cc0be81c#file-quotes-rb) that got all quotes from **Seneca**, **Marcus Aurelius**, **Epictetus**, and **Zeno of Citium**. Turns out, Workflow can parse JSON files, so I stored the result as `quotes.json` inside Workflow folder in iCloud Drive. Now I could read the file, take a random item, and use it as a quote.

<figure class="third">
  <img src="/images/posts/2018-09-02/morning.jpg" title="Morning Routine_">
  <img src="/images/posts/2018-09-02/evening.jpg" title="Evening Routine">
  <img src="/images/posts/2018-09-02/day_one.jpg" title="Day One Five Minute Journal">
</figure>

I've been practicing the routine for about a week now. I haven't noticed any significant life quality improvements yet, but I do enjoy the workflows I made, and the end results inside Day One very much.

Feel free to use and adapt my workflows as you see fit: [quotes](https://gist.githubusercontent.com/mrfoto/d57b58b017c457cd18062a1c36d82e02/raw/05211099c1843a19f2f073b4279fc3dfacacbbe4/quotes.json), [Morning Routine](https://workflow.is/workflows/c7881569dca545579b3cb121a9c1d212), and [Evening Routine](https://workflow.is/workflows/91efd3d3e26a49b081082daccac85f73).

If you have _any thoughts_, let me know in the comments or on [Twitter](https://twitter.com/MihaRekar). I'd love to talk about stoicism, journaling, or Workflow.

[^1]: They sort of do via reminders functionality but no way to get a template when you start a new entry.
