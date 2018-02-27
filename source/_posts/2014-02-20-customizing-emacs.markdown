---
layout: post
title: "Customizing Emacs"
date: 2014-02-20 14:41:30 +0100
author: Andrei Beliankou
comments: true
categories: Emacs
---

I've tried many ways to build a clean testing environment for Emacs editor on my
Ubuntu machine. One previous attempt showed a possible way to do so:

``` shell
$ emacs -Q -l some_startup_script.el
```

But this solution doesn't show the real state of affairs when we load all the configuration files in Emacs. The <code>.emacs</code> file is loaded in the middle of the Emacs initialization, not at the end. See for details [39.1.1 Summary: Sequence of Actions at Startup](https://www.gnu.org/software/emacs/manual/html_node/elisp/Startup-Summary.html#Startup-Summary). One possible problem is that <code>package.el</code> loads its configuration before you've done custom changes.

For now I consider a better way starting Emacs from another user:

``` shell
$ emacs -u emacstestuser
```

All customizations can be done in the <code>.emacs.d</code> directory from <code>emacstestuser</code>.
The only thing you need is changing of user specific variables:

``` emacs-lisp
(setq user-emacs-directory "/home/emacstestuser/.emacs.d")
```
