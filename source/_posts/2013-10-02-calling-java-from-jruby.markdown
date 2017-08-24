---
layout: post
title: "Calling Java from JRuby"
date: 2013-10-02 14:54
author: Andrei Beliankou
comments: true
categories: JRuby Ruby Java
---

How to call Java from JRuby?

``` ruby

require 'java'
java_import my.package.CoolClass

obj1 = Java::CoolClass.new

```
