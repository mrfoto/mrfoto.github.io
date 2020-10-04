---
layout: post
category: posts
title: Back Up Your Backups
excerpt: Can your backups handle a single drive failure? What about two? Three? Four in a span of just over a month?
tags: [backup, back up, backblaze, hard drives, hdd, failure, support, stoicism]
comments: true
image:
  feature: features/broken-hdd.jpg
  credit: Markus Spiske
  creditlink: https://unsplash.com/@markusspiske
---

What’s the most important thing on your computer[^1] right now? A client project? Half written master thesis? Some government document? Pictures of your childhood? Video of your kid learning how to walk? Maybe it’s that one movie you like rewatching over and over again but isn’t available to purchase anymore? Or that one demo song of a band you love when they were just starting out?

Now imagine your computer gets stolen. Poof. Gone. Can you still get these files? Are they on an external drive? When was the last time you updated the copies there? When was the last time you checked if the drive was still working?

Ah, but you say, I have my files _in the cloud_. I have some very bad news for you: file syncing services are **not backup**. Don’t believe me? Do a quick web search for the web service you use (Dropbox, Onedrive, Google Drive, iCloud, …) + “lost my files”. Yeah…

We all have tons of things we treasure on our devices and in this digital world the number of such files is only increasing. [Just in the last two years 90% of the data in the world was generated](https://www.domo.com/learn/data-never-sleeps-5). Yes, you read that right. And that number is probably not that much different for you personally.

## How I back up

A common truism you’ll come across if you go researching how you should do your backups is _two is one, one is none_. It simply means that if you have one of a thing, and that thing dies, you have none of a thing, so you should strive to have two of a thing. But a better strategy is the so called _3-2-1 rule_. It’s an easy-to-remember acronym and stands for having at least three (3) total copies of your data, two (2) of which are local but on different mediums (or devices), and at least one (1) copy is offsite.

I started getting conscious about the way I back up way back when I was starting with photography. It was often that way after I took concert pictures, the artist would contact me if they can get those photos for themselves. So, I was thinking that I better make sure I don’t ever loose those photos.

Back then I bought a Drobo Gen2, put 4 drives in, and copied all my photos there. I then took another drive, and copied all the photos up to that point to it, and took it to my grandparents home. This worked well, but I wasn’t completely satisfied, since that last drive wasn’t being updated at all. So, I was still quite exposed.

Then I moved to Ljubljana, and got access to a fast fiber network. One of the first things I got was a [Backblaze subscription](https://secure.backblaze.com/r/01gg2v) — **unlimited online backup** for $60/Computer/Year. A bargain for a peace of mind. This took care of that final check. Now all my files are on an offsite location and always up to date.

I also upgraded to [Drobo 5Dt](https://www.drobo.com/storage-products/5Dt/) because I wanted to put in another drive, and the Gen2 was getting a bit slow for my daily use. So far, so good.

## One is none. Turns out: two is none as well. And three. And even four?

It was a calm Friday afternoon on March 27 when my Drobo started making loud noises. Oh-oh. I see a red light. Meaning drive failure. First reaction: panic, cold sweat. But I repeat some stoic thoughts in my head and calm down. Drives fail. It’s normal. That’s why I have a Drobo in the first place.

Then, mere 10 minutes later, another red light. Another dead drive. This…this is not good. This is **bad**. I turn all red myself and start sweating like crazy. _Knees weak, arms are heavy_. You know the feeling. It’s not a nice one. I keep repeating stoic thoughts, but they don’t have much of an effect on me now. It’s a true showing of how much I still have to learn to practice.

My Drobo was configured to handle 2 drive failures. However, the drives that failed were the biggest ones. 2 times 8 TB that I bought together about a year back. But now Drobo was not just in recovery mode, shuffling data around, it was also out of free space. Not good. **Not good**.

<figure>
  <img src="/images/posts/2020-10-04/two_failed_drives.jpg">
</figure>

It depends on when (or where) you’re reading this, but I did not write that date just for poetic reasons. It has a meaning. Slovenia was in full COVID-19 lockdown mode. Everything was closed. Essential grocery stores were the only open businesses. Obtaining a hard drive seemed impossible. I asked Twitter for help. People suggested finding an external HDD, and taking it apart.

I went to a “superstore” chain that was open, and they didn’t have any. The clerk said they stopped selling them a while ago because no one was buying them and assures me none of their other stores have them either. But there was another brand store on the other side of the town that might have them. And indeed they did. Just one left on the shelf. So, I buy it, come home, take it apart, and stuck it in the Drobo.

<figure>
  <img src="/images/posts/2020-10-04/taking_apart_a_drive.jpg">
</figure>

The light turns green, the drive makes some spinning noises, and Drobo starts moving stuff to the new drive. Everything is still blinking orange/red, but at least the device has some space to move stuff around. Immediately I order another drive from Amazon. I learned now that I shouldn’t buy 2 drives at the same time. I also open warranty claims on Seagate for replacement of the two failed drives. Things seem to be stabilizing and I go to bed. Exhausted. Stressed out. But calmed.

The next day Drobo is still shuffling data around, but things are looking good. On the Sunday morning everything turns green. And I finally feel relaxed.

<figure>
  <img src="/images/posts/2020-10-04/drobo_status.jpg">
</figure>

I go for a run, drive for a lunch, have an overall enjoyable Sunday, and put some Netflix on in the evening. Then I hear some massive disk activity going on again. Nothing to worry, maybe [Time Machine](https://en.wikipedia.org/wiki/Time_Machine_(macOS)) is doing its thing. But it doesn’t die down. So, I go and check. **YOU GOTTA BE KIDDING ME**. The new drive that I got just failed and turn red. Drobo is again out of space and trying to move data around to protect it. I panic and turn it off.

About a week later I get Seagate replacement drives. They replaced it with refurbished ones. Which is understandable, but concerning when it comes to hard drives. Still, I stick them in, turn the Drobo back on, and 2 days later everything is green again and I have the same drive capacity as I did before.

<figure>
  <img src="/images/posts/2020-10-04/drobo_status_back_to_normal.jpg">
</figure>

A week passes. Two weeks. I almost feel like nothing happened and everything is back to normal. Then I hear some rumblings and a red light. Another drive failure. One of the replacement ones.

I take a deep breath and start writing a message to Drobo support. One drive failing? OK. Two? Yeah, I guess they’re from the same series. The third one? A brand-new one? Just after a day? OK, blame it on the U curve[^2]. But a brand-new replacement one? Which was surely thoroughly tested by the Seagate factory before sending it out **as a replacement**?  That **has to be** a device issue.

We go back and forth, I provide all the logs and exports, and they are certain it’s not the device, but the disks. Which all makes sense but I’m still unconvinced. I explain that I’ve completely lost faith in this device and that I’m afraid of losing my data. They understand and come through and send me a replacement Drobo.

On May 21 I receive the replacement. I take the drives from the old one, together with a replacement for the replacement (ha!) that I received in the meantime, and turn it on. It chugs along for a couple of hours and then it all turns green. Haven’t had a problem since.

<figure>
  <img src="/images/posts/2020-10-04/drobo_replacement.jpg">
</figure>

Was it the device? Was it just the hard drives? I’ll never know. But things have been green ever since. It’s October 4 when I’m writing this, and the Drobo has been up and running all green pretty much all the time since then, so I’m fairly certain things are good now. Until the next failure…

## Aftermath

It took a while for me to write this blog post. I needed some emotional distance, I guess. My files were never truly at risk, there was always that _-1_ part option of _3-2-1_ — the Backblaze backup. But that’s more of a “worst-case scenario” option. It’s great to have it, but if possible, you don’t want to use it. I have over 6 TB of data and downloading that is no fun even over a fast fiber connection. Plus you have to have a place where you _download files to_.

## What is your back up situation like?

Could you handle a single drive failure? What about two? Three? Four in a span of just over a month? What if your apartment floods? Or if your laptop gets stolen? Do you have an off-site drive? When was the last time you updated the data there?

Digital data doesn’t take any physical space but it can hold immense emotional value. You’d pay **a lot of money** to get lost photos of your kid back. But you can protect them for a fraction of that today. Hard dives have gotten extremely cheap. [Backblaze](#) is not expensive either. Don’t let your penny-pinching today make you pound-foolish in the future.

What happened to me is extremely unlikely. But it can happen. It did happen. I was prepared[^3]. Are you?

[^1]:	Smartphones are computers too. They’re [more powerful as well](https://twitter.com/dhh/status/1174802413548474368) 😅
[^2]:	Hard disks (and pretty much all other devices) follow a U shaped failure rate. They either die when they’re brand new, or they die after they’ve been at it for a long timee.
[^3]:	physically, not emotionally though
