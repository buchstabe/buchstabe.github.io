---
lang: en
permalink: /en/notebook/:year/:month/:title.html
layout: post
title: "Adding ignored files with Git"
date: 2014-02-12 13:09
author: Andrei Beliankou
comments: true
categories: Git
---

Today I've encountered the problem adding files within a LaTeX project.
All generated PDF files are ignored in the project <code>.gitignore</code>:

``` shell
$ cat .gitignore
*.pdf
```

I had to add two PDF files with graphics and didn't want to change my ingnoring rules:

``` shell
$ git add -f file1.pdf file2.pdf
```

The <code>-f</code> switch forces Git to add ignored files. Use it!
