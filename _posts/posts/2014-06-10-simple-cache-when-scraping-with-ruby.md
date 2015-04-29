---
layout: post
category: posts
title: Simple Cache When Scraping With Ruby
excerpt: Use VCR in your scraping development workflow.
tags: [ruby, rails, scraping, cache, scrape, cassette, vcr]
comments: true
---

I'm scraping a bunch of websites lately and got bored with using `File.write` to store cached versions of websites. Because I'm still developing the script I don't want it to hit the real website every time. So simple way to fix that is with the [vcr gem](https://github.com/vcr/vcr). While made primarily for testing you can also use it for this kind of tasks.

First you need some kind of configuration file that loads before your actual script. I have it in `config/vcr.rb`:

```ruby
VCR.configure do |c|
  c.cassette_library_dir = 'cassettes'
  c.hook_into :webmock
  c.allow_http_connections_when_no_cassette = true
end
```

Then I have a `Shared` module with the `cache` method which I `include` in any classes I need this functionality:

```ruby
module Shared
  def cache name
    VCR.use_cassette name do
      yield
    end
  end
end
```

And now you can use this magic, to have the website you're scraping instantly cached:

```ruby
def github_for user
  cache "gh-#{user}" do
    response = open("https://api.github.com/users/#{user}").read
    JSON[response]
  end
end
```
