---
lang: en
permalink: /en/notebook/:year/:month/:title.html
layout: post
title: "Deleting files from a Git repository"
date: 2013-07-13 15:28
author: Andrei Beliankou
comments: true
categories: Git
---

Suppose you have been working for a long time on a project, and now you want to delete some files from you project because ... (the reason does not really matter at this point).

You may want to completely erase a file or a whole directory from your repository. The file or directory may be kept in the local copy or deleted as well.

If you want a complete removal use <tt>git rm</tt>:

``` shell

$ git rm file_to_delete.rb
$ # file_to_delete.rb removed from both your working copy and repository tree.
$ git rm -r directory_to_delete
$ # directory_to removed from both your working copy and repository tree.

```

``` shell
If you want to keep your local copy use <tt>git rm --cached</tt>.
$ git rm --cached file_to_delete.rb
$ # file_to_delete.rb removed only from repository tree.
$ git rm --cached -r directory_to_delete
$ # directory_to removed only from your repository tree.

```

In the latter case don't forget to add the file or directory to your <tt>.gitignore</tt> file, otherwise _Git_ will bother you with annoying status messages.

One last thing you should keep in mind is that erasing data from a repository means only that the information is not present in the actual commit and in all future incarnations of the code. The data can be restored from the previous states of your repository. If you want to wipe your sensitive data consider reading the appropriate [GitHub Help page](https://help.github.com/articles/remove-sensitive-data) on this topic.
