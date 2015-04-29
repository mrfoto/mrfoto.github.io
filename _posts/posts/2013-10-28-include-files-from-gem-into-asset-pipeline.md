---
layout: post
category: posts
title: Include Files from Gem into Asset Pipeline
excerpt: Sometimes Asset Pipeline doesn't want to play with you.
tags: [ruby, rails, gems, pipeline, precompile, precompilation, asset pipeline, svg, sprockets, assets]
comments: true
---

I've spent a good hour debugging why the **.svg** file from my [swipebox gem](https://github.com/mrfoto/swipebox) wasn't being precompiled by the **Rails Asset Pipeline**. I'm still not sure why, because it works with .svg fonts but for some reason it didn't want to "grab" the swipebox-icons.svg file.

The way I solved is I added an **initializer** to my Engine class which adds all the images (just in case) to the `config.assets.precompile` setting:

```ruby
module Swipebox
  class Engine < ::Rails::Engine
    initializer 'swipebox.assets.precompile' do |app|
      app.config.assets.precompile << %r(swipebox-[\w]+\.(?:png|svg|gif)$)
    end
  end
end
```

Hope it helps someone :)
