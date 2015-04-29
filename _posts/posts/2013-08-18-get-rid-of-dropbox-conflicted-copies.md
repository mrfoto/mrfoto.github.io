---
layout: post
category: posts
title: Get Rid of Dropbox Conflicted Copies
excerpt: They can be such a pain in the ass.
tags: [dropbox, conflicted, conflicts]
comments: true
---

If you are like me and have multiple computers with spotty internet connection this happens all the time.
#Warning: This will **delete** your conflicted copies

If you are not sure about deleting them, **DON'T**

```bash
find ~/Dropbox/ -path "*(*'s conflicted copy [0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]*" -exec rm -f {} \;
```

If you just want to find out about your conflicted copies, then run this:

```bash
find ~/Dropbox/ -path "*(*'s conflicted copy [0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]*" -print
```
