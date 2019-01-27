---
author: Andrei Beliankou
lang: en
permalink: /en/notebook/:year/:month/:title.html
layout: post
title: "Capistrano deployment strategies: deploy via a copy"
date: 2013-02-24 18:39
comments: true
categories: Ruby Deployment
---

[Capistrano](https://github.com/capistrano/capistrano) presents a very
convinient way to manage your remotely deployed applications and
websites. It has initially been developed for Rails deployment. But it
also can be very useful for static site deployment.

<!-- more -->

I've been using Capistrano for a couples of months, but I have still
some question open. Everything seems to be simple and clear if you
grasp main ideas behind the deployment.

One of the buzzing topics is how the source code of your applications
gets onto the remote machine. There are two ways for that. The source
code can be either uploaded from your local machine, where the
Capistrano deployment script is executed, or the remote server
(dedicated for the deployment) can fetch the code from an scm
repository which should be accessible remotely in this case.

Capistrano supports the idea of deployment strategies. Strictly
speaking they are the way, how the source code goes to the remote
machine. We can distinguish between <strong>local</strong> and
<strong>remote</strong> strategies.

Local strategies have only one representant, the <strong>copy</strong>
strategy. Remote strategies split into <strong>export</strong>,
<strong>checkout</strong> and <strong>remote_cache</strong> variants.

The above text means: if you're using a local scm repository which
cannot be accessed from the remote machine, you can use only the copy
strategy. In that case you use the code:

``` ruby
	set :deploy_via, :copy
```

For more details consider to read the Capistrano source code:
[https://github.com/capistrano/capistrano/tree/master/lib/capistrano/recipes/deploy/strategy](https://github.com/capistrano/capistrano/tree/master/lib/capistrano/recipes/deploy/strategy)

You may be also interested in this article about deployment of static
files:
[http://f3internet.com/articles/2010/06/18/deploying-static-sites-with-capistrano/](http://f3internet.com/articles/2010/06/18/deploying-static-sites-with-capistrano/)
