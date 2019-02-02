---
lang: en
permalink: /en/notebook/:year/:month/:title.html
layout: post
title: "Using sudo for system administration"
date: 2014-02-14 16:37
author: Andrei Beliankou
comments: true
categories: sudo
---

We can face the situation with restricted rights on a server. This is a use case for <code>sudo</code>.
You can get restricted access to specific commands as <code>root</code>, but not to the whole system, which is very good!

I need access to <code>virt-top</code> to monitor kvm based virtual machines on a big host system. Add the following line to <code>sudoers</code> file:

```
myusername ALL= NOPASSWD: /usr/bin/virt-top
```

This line allows <code>myusername</code> to run <code>virt-top</code> without password from any terminal.

A couple of useful links:

* http://www.komar.org/pres/sudo/toc.html
* http://www.sudo.ws/sudo/sample.sudoers
* http://www.garron.me/en/linux/visudo-command-sudoers-file-sudo-default-editor.html
