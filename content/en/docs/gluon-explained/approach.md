---
title: "Approach"
description: "An explanation into Gluon's general approach."
lead: "An explanation into Gluon's general approach."
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

Gluon focuses on:
- Easier, simpler, faster development
  - New approaches for APIs like IPC being batteries-included and as intuitive and easy to use as possible
  - Apps are "just" Node scripts you can run, no having to use an external app/binary
  - Removing as much boilerplate as possible
- Enhancing developer and user choice
  - Using almost any system installed browser
  - Firefox support
  - Deno/Bun support (WIP)


### General API Structure

**Instead** of using functions to get and set like:

```js
// Gluon does not do this
await Window.page.getTitle(); // Get current page title
Window.page.setTitle('new title'); // Set page title
```

Gluon generally uses getters and setters (or `Proxy`s) where possible, as, in our opinion, it makes code simpler and generally cleaner:

```js
// Gluon does this
await Window.page.title; // Get current page title
Window.page.title = 'new title'; // Set page title
```

Whilst this may be confusing for some to begin with, we believe this unique approach benefits developers in the end. There are also often alternative functions as well in some APIs where it may be more confusing, although not encouraged.