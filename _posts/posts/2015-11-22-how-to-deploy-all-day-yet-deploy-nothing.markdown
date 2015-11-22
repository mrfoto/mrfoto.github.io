---
layout: post
category: posts
title: How to Deploy All Day yet Deploy Nothing
excerpt: Docker is not as easy as they would have you believe
tags: [docker, aws, elastic beanstalk, heroku, devops, rails, otto]
comments: true
---

We had great weather the whole November. When it turned bad yesterday I finally had a chance to work on an app idea I had long been thinking of. You know the drill: `rails new`, replace `sqlite` with `pg`, add `devise` and `rspec`. I also wanted to play around with cool things I've been hearing of so I've added `pundit`, `administrate`, and `bower`. Write a couple of migrations, and *voila*, the famous [rails app under 15 minutes](https://www.youtube.com/watch?v=Gzj723LkRJY) still holds true **10 years** later.

Speaking of cool things - [Docker](https://www.docker.com/) is one of the coolest kids on the block. *Many articles, such blog posts, much tools, very containers, wow*. I wanted to try it out for a long time now. This greenfield typical rails app felt like the perfect place. No complex code or crazy gems, practically empty. **Thousands** developers must have deployed the **exact same thing** many times before. What could *possibly* go wrong?

I've googled and googled, used *Search tools* to limit time frame, and skimmed through hundreds of posts. After all that I had a rough idea in mind what I'll need to do. I've narrowed down a couple of great[^1] posts and tried to follow their instructions.

As with every cool new technology - things change. **Crazy fast**. The majority of posts you come across are outdated. Not to mention contradicting. To even get docker running locally was a pain. All the posts use `boot2docker` which has *obviously* been replaced by `docker-machine`. Luckily `brew` knows everything[^2].

[Running Rails with Docker](https://blog.codeship.com/running-rails-development-environment-docker/) by @mlocher seemed like a great place to start. I ran the *very first command* `docker build -t demo .` and immediately got the most self-explanatory error ever:

> `Cannot connect to the Docker daemon. Is the docker daemon running on this host?`.

**Wat**!? As mentioned above, things in dockerland move with crazy pace so even Stack Overflow has problems following. Eventually I figure out I have to `docker-machine create --driver virtualbox dev` and `eval "$(docker-machine env dev)"`. *Naturally*.

I can build images now. I dive into `Dockerfile` and customize it to my needs. Actually this was the most straight-forward step of them all. It actually makes sense. Simple DSL with good naming - this Docker thingy was bumpy at the start, but now *I'm on a horse*. I write it, I build it, I run the container, everything works. Well everything but PostgreSQL. I can figure this out later I remembered reading in another blog post.

OK, so let's deploy this on Elastic Beanstalk. [I've heard](http://sebastien.saunier.me/blog/2015/10/20/aws-elastic-beanstalk-commands-for-rails.html) it's like Heroku, only **better**. I decide to follow recent and well written @jtescher's [How to set up a Rails app with Elastic Beanstalk and PostgreSQL](https://medium.com/@jatescher/how-to-set-up-a-rails-4-2-app-on-aws-with-elastic-beanstalk-and-postgresql-3f9f29c046e2). Sure it's not for Docker *specifically*, but should be *same same but different*, right?

`eb init` immediately recognizes that I have a Docker project. It asks where I want this, creates some config files, *wow* this feels like **actual progress**. Next - `eb create` launches, looks promising, works for a looong time, aaaaand nothing. Errors galore. There is no way to `tail -f` log while it's deploying, because the thing runs inside of a container inside of Beanstalk. But I can get the last 100 lines of logs in AWS Console.

I figure out I'm missing `ENV['SECRET_KEY_BASE']`. Ah, no biggie, I'll just set the config var. But I **can't** do that if container is down. And it's down because the config var is **missing**. Right. OK, I got this, I'll delete the eb environment  and start again. God, why does everything take soooo loooong on aws. Creating, deleting, I can feel myself getting older.

Wooo, app starts now, I see the app error on the world wide web. I know this error means db is missing and we're on AWS so we have RDS. Couple of clicks and this will just work is what I read in them blog posts. Click, click, click,…

>DBSubnets: Invalid option value

**Wat**!? I explicitly selected the only 2 options it offered me. *Google, Google on the wall: What's this stupid error for?* Looks like an AWS issue and they [know about it](https://forums.aws.amazon.com/message.jspa?messageID=678379#678379).

Fine, I'll create the db in RDS and just link it in eb…nope, doesn't work. Gah! But they say `eb` is smart enough to do this *when creating a new environment*. I know the drill by now - delete the env, wait, create env with `--database.engine postgres`, wait, wait, wait, done.

App still errors :confused:. So there goes another 30 mins of googling to figure out how to `ssh` to eb so I can `ssh` to running docker container so I can `tail -f`. *Inception*.

Ah, it didn't run migrations. I did read in a post somewhere that it should do this by itself so it must have been true. Ah, that only applies to *eb rails*, not *eb docker*. Got it.

How do I run migrations then? `Dockerfile` won't work because container does not run yet when they are executed. `container_commands` are run

>after the application and web server have been set up and the application version file has been extracted, but before the application version is deployed

That's too early as well. There is an answer by an [aws employee](https://forums.aws.amazon.com/message.jspa?messageID=666973#666973) to write a tmp file on a leader only. Then mount that in `Dockerfile` and

> simply check the existence of such marker file and run leader only initializations

A bit more googling and I end up with `(test -f /tmp/is_leader && bundle exec rake db:migrate) ; bundle exec puma -C config/puma.rb`. *Simple*, right? Yeah, I don't think so either.

Anyway, let's `eb deploy` again. Health OK, migrations run, app shows up, wooooo :tada:. But, wait…where are the **assets**? I *know* bower ran, I *know* `rake assets:precompile` ran, so WTF!?

Again `eb ssh`, `docker ps`, `sudo docker exec -i -t [container_id] bash`[^3], `cd app/public`. Yup, they're there. Must be something…aaah, `nginx` is not serving them. FFFFFFFUUU…

By this point it's *11:30PM*. My girlfriend walks in and asks me what I'm doing. I explain I've wasted the whole day exploring new things and concepts and I *really* don't want to learn how `nginx` config works now. I say that if I'd deploy this to [Heroku](http://heroku.com/) I'd be done in 10 min - or in other words - **~12 hours ago**.

Just to prove my point I do `heroku create`, `git push heroku master`. And it **fails**. **Wat**!? Ah, I need to run `bower` first. Awesome [Heroku docs](https://devcenter.heroku.com/) to the rescue and I do `heroku buildpacks:add --index 1 heroku/nodejs`, `git push heroku master`, `heroku run rake db:migrate`, `heroku open`. Bam - everything there, everything works. Under 10 mins even. Now I can go to bed.

---

So what's this rant about? Web development is **hard**. *Just* figuring out Rails is hard. There's Ruby, ERB (HTML), CoffeeScript (JavaScript), SCSS (CSS), Active (Support, Model, Record, Job), Action (Pack, View, Mailer),…and that's just scratching the surface[^4].

Now I didn't expect deployment to be *Heroku* easy. Not at all. But I didn't expect I wouldn't be able to figure out how to deploy a **standard** rails app in the whole day either.

There are new things like [`otto`](https://ottoproject.io/) coming though. There was a [great episode](http://5by5.tv/changelog/180) of The Changelog with @mitchellh explaining it. In theory it should figure everything out on it's own and *just work* with `otto deploy`. Of course I've tried it but it's [not there yet](https://github.com/hashicorp/otto/issues/330).

Software moves with *blazing speed* and if you don't follow it closely you're quickly stuck far behind. Blog posts rarely help since they're mainly written when someone is learning (like this one). But once they figure it out it becomes second nature so they think that *everyone* knows how to do it and see no point in writing another post.

A lot could be improved though. Docker should have **better docs** with more **actual examples** and update them **regularly**. I know this is *hard work* but it's something they have to do if they want their technology to spread even further. To *regular* developers who don't have a couple of days to figure it out.

And let's not even go into how confusing AWS console UI is. Yes they offer a ton of services, but **seriously**?

<figure>
  <img src="/images/posts/2015-11-22-aws-console.png">
</figure>

[I know nothing, but I learn, I learn](https://www.youtube.com/watch?v=s6EaoPMANQM).

[^1]: in my humble opinion
[^2]: seriously, [Homebrew](http://brew.sh/) is **the shit**
[^3]: you would think they would have something like `docker ssh [container_id]`, right? I mean, everybody needs this :confused:
[^4]: [This is Why Learning Rails is Hard](https://www.codefellows.org/blog/this-is-why-learning-rails-is-hard)
