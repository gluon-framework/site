---
title: "Controls"
description: "The Controls Window API (Window.controls)"
lead: ""
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "window api"
weight: 303
toc: true
---

## `minimize()`
Minimize the browser window.

### Examples

<div class="glow" style="--glow-hue: 320">
<div class="filename node">index.js</div>

```js
Window.minimize(); // Minimize the window
```

</div>
<div style="margin-bottom: 60px"></div>

## `maximize()`
Maximize the browser window. Does not show it, run `show()` additionally before to ensure it's visible / pops up.

### Examples

<div class="glow" style="--glow-hue: 320">
<div class="filename node">index.js</div>

```js
Window.maximize(); // Maximize the window
```

</div>
<div style="margin-bottom: 60px"></div>

## `show()`
Show (unminimize) the browser window.

### Examples

<div class="glow" style="--glow-hue: 320">
<div class="filename node">index.js</div>

```js
Window.show(); // Show the window
// Window.maximize() // Also maximise it after
```

</div>
<div style="margin-bottom: 60px"></div>
