---
title: "Architecture"
description: "A deep dive into Gluon's architecture."
lead: "A deep dive into Gluon's architecture."
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "gluon-explained"
weight: 100
toc: true
---

### Overview

Gluon's architecture is relatively simple:
- **JS backend** (Node script/app managing the Window)
- **Web frontend** (browser window)

<br>

Compared to Electron's process model, Gluon is simpler as it skips having a preload. This simplifies learning and the development process, plus leads to more efficient resource usage, by not having to use 2 IPC layers.
