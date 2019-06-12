---
layout: post
title: "Compare Words not Lines!"
permalink: /en/notebook/:year/:month/:title.html
date: 2012-06-11 22:48:47 +0200
comments: false
categories: TIL
author: Andrei Beliankou
---

Git can show a diff comparing words and not lines.

The default comparison in Git is aimed on a line per line difference.

Having a file with a typo we get the standard not useful comparison:

``` shellsession
$ git diff
diff --git a/file.txt b/file.txt
index 372092b..7778d0f 100644
--- a/file.txt
+++ b/file.txt
@@ -1 +1 @@
-This is a long line with a tyop.
+This is a long line with a typo.
```

Use `git diff --word-diff` to get visually appealing comparison:

``` shellsession
$ git diff --word-diff
diff --git a/file.txt b/file.txt
index 372092b..7778d0f 100644
--- a/file.txt
+++ b/file.txt
@@ -1 +1 @@
This is a long line with a [-tyop.-]{+typo.+}
```
This approach is extremely useful for comparing changes in text documents like Markdown or LaTeX.

Compare words, not lines!
