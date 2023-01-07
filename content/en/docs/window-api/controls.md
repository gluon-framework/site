---
title: "Controls"
description: ""
lead: ""
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "gluon api"
weight: 303
toc: true
---

## `minimize()`
Minimize the browser window.

### Examples

```js
Window.minimize(); // Minimize the window
```

<br>

## `maximize()`
Maximize the browser window. Does not show it, run `show()` additionally before to ensure it's visible / pops up.

### Examples

```js
Window.maximize(); // Maximize the window
```

<br>

## `show()`
Show (unminimize) the browser window.

### Examples

```js
Window.show(); // Show the window
// Window.maximize() // Also maximise it after
```
