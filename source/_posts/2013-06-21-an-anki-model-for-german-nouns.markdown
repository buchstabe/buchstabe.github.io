---
lang: en
permalink: /en/notebook/:year/:month/:title.html
layout: post
title: "An Anki Model for German Nouns"
date: 2013-06-21 11:47
author: Andrei Beliankou
comments: true
categories: Anki DaF
---

[Anki](http://ankisrs.net/) is a great software piece dealing with [Spaced Repetition](http://en.wikipedia.org/wiki/Spaced_repetition).

The second generation of Anki offers a different view on cards, notes, facts and layouts. Compared to the first version of this program, one may be confused by alternating definitions. But after a short period everything gets clear and logical.

I learn German nouns with my custom note type *GermanNoun*. It exposes the following fields:

  * Wortform;
  * Artikel;
  * Aussprache;
  * Paradigma;
  * Bedeutung;
  * Beispiel.

The trick is to combine these field with the help of card layouts. Using only 6 fields (many of them can be ommited) we are going to generate a lot of useful card.

Here the examples of the front card side:

```
    {{Wortform}}
    <br>
    {{Beispiel}}{{Beispiel}}{{Beispiel}}

```

```
    The corresponding back side can be encoding as follows:

    {{Artikel}} {{Wortform}}
    <span style='color: red; font-size: 16px'>{{Paradigma}}</span>
    <br>
    {{Aussprache}}{{Aussprache}}{{Aussprache}}
    <hr id=answer>
    {{Bedeutung}}
```

You may want to experiment with colors and font properties. HMTL to rescue :)
