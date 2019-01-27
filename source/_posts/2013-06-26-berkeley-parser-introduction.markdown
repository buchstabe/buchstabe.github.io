---
lang: en
permalink: /en/notebook/:year/:month/:title.html
layout: post
title: "Berkeley Parser: Introduction"
date: 2013-06-26 12:27
author: Andrei Beliankou
comments: true
categories: Parsing NLP
---

[Berkeley Parser](https://code.google.com/p/berkeleyparser/) is one the best open source syntactic parsers for today. It uses a sofisticated split-merge algorithm to learn a constituent grammar started with a simple x-bar grammar.

The parser itself and a grammar for one of provided languages here from its [repository](https://code.google.com/p/berkeleyparser/downloads/list) at Google code. For now pretrained grammars are offered for English, German, French, Bulgarian, Arabic and Chinese.

We've downloaded the parser archive and the English grammar. Let's try to produce some meaningful output:

``` shell
$ echo "The horse raced past the barn fell ." | \
$ java -jar BerkeleyParser-1.7.jar -gr eng_sm6.gr
```

The resulted analysis is by far not ideal but it is a good beginning:
