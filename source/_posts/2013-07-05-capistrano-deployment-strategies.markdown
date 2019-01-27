---
lang: en
permalink: /en/notebook/:year/:month/:title.html
layout: post
title: "Capistrano: deployment strategies"
date: 2013-07-05 12:57
author: Andrei Beliankou
comments: true
categories: Capistrano Ruby Deployment
---

[Capistrano](http://www.capistranorb.com) is a  tool for remote server _automation_ and _deployment_. We have to underline these two task as they will remain two different areas for a long time. Historicaly *Capistrano* was a deployment tool, but since then many server administration tools have been created for remote server administration. Software installation, package upgrade, data base management can be arranged using *Capistrano*.

Capistrano supports the idea of deployment strategies. Strictly speaking they are the way, how the source code goes to the remote machine. We can distinguish between _local_ and _remote_ strategies.

Local strategies have only one member, the _copy_ strategy. Remote strategies split into _export_, _checkout_ and *remote_cache* variants.

If you have a static site or do not want to use a SCM for deployment look at the following code snippet:

``` ruby
set :repository,  "./source_dir" # This is our directory with the content to be deployed.
set :scm, :none # Do not use any SCM.

set :deploy_to, '/var/www/mysite/htdocs' # This is a place on the remote machine.
set :deploy_via, :copy # We are going to deploy using the copy strategy.

set :copy_dir, './tmp/capistrano' # Here we create a temporary archive with our content.
set :copy_remote_dir, "#{deploy_to}/tmp/capistrano" # There the archive will be copied.

```

You have to ensure that both local and remote directories for archives exist.

If you need some additional readings on *Capistrano*, try out the following:

  * [Capistrano Home Page](http://www.capistranorb.com)
  * [stackoverflow questions on Capistrano](http://stackoverflow.com/questions/tagged/capistrano)
  * [Source Code](https://github.com/capistrano/capistrano)
  * [Wiki](https://github.com/capistrano/capistrano/wiki)
