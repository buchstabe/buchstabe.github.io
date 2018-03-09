---
layout: post
title: "How to install Zotero Standalone on Linux"
date: 2018-03-09 19:38:35 +0100
comments: true
categories: Zotero
---

# How to install Zotero Standalone on Linux

[Zotero](https://www.zotero.org/) is our favorite research tool and the means how we work on bibliography collections.

As of today Zotero is not distributed any more in form of a Firefox plugin. The fifth version of this popular bibliography manager replaced the former _standalone_ version.

Since most of us have a Linux based laptop we need to install Zotero without the official installer.

Zotero can be installed from packaged sources:

- [Zotero as a SNAP](https://github.com/ibaidev/zotero-snap);
- [Zotero Installer as DEB package](https://github.com/smathot/zotero_installer).

We will try to install Zotero from the official sources:

- Download the official archive ([https://www.zotero.org/download/](https://www.zotero.org/download/));
- Uncompress the archive under `~/.local/opt/`;
- Link the Zotero executable under a directory in your `$PATH`, e.g.:

``` shell
$ ln -s ~/.local/opt/Zotero_linux-x86_64/zotero ~/.local/bin/zotero
```

- Start Zotero from the console, lock the program icon to the launcher, which creates a launcher copy under `~/.local/share/applications/zotero.desktop`.

That's it!
