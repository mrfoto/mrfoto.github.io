---
layout: post
category: posts
title: Rails Routing and Namespaced Models
excerpt: Namespaces can bite you but they're still nice.
tags: [ruby, rails, routing, routes, namespace, module, relative model naming, naming]
comments: true
---

If you're like me, you like code neatly organized in folders. With Rails we can simply do that with module namespaces. So lets say we have generated a scaffold `Projects::Document`. Now when using `url_for` or `form_for` or any other path|url helper Rails would return the namespace in the route name like so: `projects_documents_path`.

Sometimes you don't want that, especially if you nest those resources. I for example have it nested under Project so Rails wants to find `project_projects_documents_path`. That's just too confusing and serves no real purpose.

I [found](http://codecolossus.com/blog/2011/05/01/active-model-name-and-resources.html) a hard and hackish way to get rid of that using the `self.model_name` method in the model and have it return `ActiveModel::Name.new(self, nil, "Document")` but I didn't like the solution because it really looks hackish and I had to do it in all the namespaed models.

But fortunately there is an easy way to solve that. It's not documented anywhere and I don't know why but it sits nice in the [source](https://github.com/rails/rails/blob/e1f4f644344199bba7a060fe1ad27cde2e8d81e9/activemodel/lib/active_model/naming.rb#L231). All you have to do is define a `self.use_relative_model_naming?` in your module and have it return `true` like so:

```ruby
module Projects
  def self.use_relative_model_naming?
    true
  end
end
```

Now Rails searches for `project_documents_path` and [all izz well](http://www.youtube.com/watch?v=Hy3rPcoC2vA).
