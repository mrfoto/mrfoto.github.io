---
layout: post
category: talks
title: Neo4j for RubyC Hipsters
excerpt: The first proper conference talk I did. An updated and improved version of the other Neo4j hipster talk. And some words on RubyC and Kiev.
tags: [ruby, rubyc, kiev, ukraine, neo4j, graph, databases, hipster]
comments: true
---

I wanted to do a proper conference talk for a while now. I've sent a lot of proposals to conferences I found on [rubyconferences.org](http://rubyconferences.org/).  So far only one got accepted - at [RubyC](http://rubyc.eu/). I was sort of surprised but that meant I'll be going to Ukraine for the first time so I was really looking forward to that. The day came and I gave the talk and now came home and I just can't get over how awesome everything was.

The speaker lineup was great - and since now I was one of them it meant that I got to hang out with the coolest people ever all the time. Their talks were great as well.  My new boss @bbatsov did a talk on the bad parts of Ruby and what we can do to fix them ([slides](https://speakerdeck.com/bbatsov/ruby-the-bad-parts)). @sferik blew everyone away with simplicity and speed of the [Crystal](http://crystal-lang.org/) language. @juliancheal made everyone want to hack on new *internetofthings* toys. @ahoward made us all feel bad about what we're doing ([but in a good way](https://www.evernote.com/shard/s76/sh/98d3827c-6f66-4886-97cc-70ff242f3c78/509d124a169a7c33)). And @benlovell did the best closing talk possible.

There were some weird talks as well - with English slides but in Ukrainian (Russian? idk). I had no idea what they were about which is sad, because slides looked interesting. Organizers should have forced them to speak English, like we do at @RubySlovenia lately. A talk done in bad English has a **much** wider audience than a talk done in a local language (unless your local language *is* English).

Kiev (Kyiv) was awesome as well. And sooo cheap. *Really*. The metro though - I have to rip Ben off - it's in the damn core of the Earth. Seriously. I am **NOT** joking. [Check it out](https://www.youtube.com/watch?v=BabVvt0AC7M). Those escalators go at like twice the speed of regular ones, yet it still takes this guy almost 5 minutes to get out. **Insane**.

Onwards to my talk. There are slides and video below. I first talked about Neo4j and then shown some examples of Cypher via the web UI. I used the [classic movie db](http://neo4j.com/developer/example-data/) to show how nodes, relationships, and properties actually look/work. They were totally blown away when I double clicked on an actor node and movies and relationships just popped up. After that I presented the [neo4hub](https://github.com/mrfoto/neo4hub) "project" which is more or less just an importer of data from GitHub API to my Neo4j models. We did some cool queries on that, but I have a hard time remembering them. There are some cool examples in the repo so if you're interested go ahead and clone the repo, import data, and click around. Anyway you can see the live demo in the video so I suggest you watch it. Cause it's really cool :grin:.

I got great responses during and especially after the talk (both immediately and later at after parties). I guess there will be a lot of Ukrainian developers trying out Neo4j in the future. At least for their hobby projects so they get a grip on it. That was my advice actually. By the way - so should **you**. Give Neo4j a try.

Anyway, thanks again to RubyC organizers for letting me do a talk. I had a blast.

## Video:
<iframe width="width:100%" src="https://www.youtube.com/embed/STtpYx1aUHg" frameborder="0" allowfullscreen></iframe>

## Slides:

<script async class="speakerdeck-embed" data-id="8e1e9e584f674c7887e42477aea1018d" src="//speakerdeck.com/assets/embed.js"></script>

## More good things on neo4j:

- [Neo4j Official Site](http://neo4j.com/)
- [Neo4j meets Ruby](http://www.neo4j-ruby.org/)
- [New Neo4jrb documentation](http://neo4jrb.readthedocs.org/en/latest/)
- [Introduction to Graph Databases](https://www.airpair.com/neo4j/introduction-graph-databases)
- [Embracing Reality with Neo4j](http://nosqlasia.org/blog/embracing-reality-with-neo4j)
