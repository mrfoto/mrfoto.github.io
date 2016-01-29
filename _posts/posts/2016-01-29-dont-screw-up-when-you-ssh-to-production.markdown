---
layout: post
category: posts
title: Don't Screw up When You SSH to Production
excerpt: Terminal can help you with colors
tags: [ssh, zsh, bash, iterm, iterm2, terminal, mac, color, tab, profile]
comments: true
---

Do you `SSH` to production? Do you do it to figure out why a particular bug is happening? Do you mimic same actions locally to narrow that nasty bug down? If so, did you ever do something on the production server that you planned to do on the local one?

I'm guessing the answer is **yes** and not just once otherwise you wouldn't be reading this. If you've been a web developer even for a small amount of time this is a part of life. You've been debugging for a while so you lose focus. At one moment you see that you screwed up and you sweat up like crazy :cold_sweat: After realizing what you've done you can only hope that you didn't do too much damage and that it can all be reverted.

**But it doesn't have to be like that**. So the last time this happened to me I started looking if there's anything that would visually distinguish which of my tabs is connected to production. I started looking around and found a way to change that tab color. But I also found a way to change the profile automatically. About an hour of copy/pasting and experimenting later and this is what I ended up with:

![SSH in color](http://i.imgur.com/B8Dw0O2.gif)

Notice that the tab and profile color change the moment I `ssh` to the server. And it automagically goes away as soon as I exit it. Isn't this awesome?

I'm on a Mac using the fantastic [iTerm2](anything and everything that has textboxes) with [oh-my-zsh](http://ohmyz.sh/) but with a bit of *googling* you can modify the following script to work for your setup as well.

<script src="https://gist.github.com/mrfoto/c6072e4fede3a6fe0f6b.js"></script>

OK, so what do we have here? Basically we alias `ssh` with `colorssh`. And that one checks if the server we're connecting to is one of the production ones (in this sample script they are `web*`, `production`, and `ec2-.*compute-1`). If that is the case then it changes iTerm2 profile to `SSH` and tab color to red.

If you have the same setup as me then just place the above script in `~/.oh-my-zsh/custom`, and create profile with the name `SSH` in iTerm2. You can find lots of great color schemes [here](http://iterm2colorschemes.com/).

On a different setup you'll have to do some investigating work on your own. But it can all be done even with plain bash and regular Terminal. I derived my script from:

- [Change terminal color when SSH from OS-X](https://coderwall.com/p/t7a-tq/change-terminal-color-when-ssh-from-os-x)
- [Mac OS X Terminal: visual indication for your ssh connection](http://www.rngtng.com/2011/01/14/mac-os-x-terminal-visual-indication-for-your-ssh-connection/)
- [iterm2-ssh-color-scheme](https://github.com/hectorleiva/iterm2-ssh-color-scheme)
- [Change iTerm2 tab color when using SSH](https://gist.github.com/wadey/1140259)
- [Changing terminal color in MacOSX when SSHing](https://gist.github.com/porras/5856906)
