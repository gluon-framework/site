---
title: "Page"
description: "The Page Window API (Window.page)"
lead: ""
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "window api"
weight: 302
toc: true
---

## `eval(expression)`
Evaluate JS in the Web frontend and return the result. If there's an error, it will return it like the window usually would (like `ReferenceError: notDefined is not defined`).

### Arguments

#### Expression
JS to evaluate, either as a function or string.

### Examples

<div class="glow" style="--glow-hue: 320">
<div class="filename node">index.js</div>

```js
// Get the current url of the document
const currentUrl = await Window.page.eval(`location.href`);
```

</div>
<div style="margin-bottom: 60px"></div>

## `loaded`
A Promise which is resolved when the page loads (like `window.onload`).

### Examples

<div class="glow" style="--glow-hue: 320">
<div class="filename node">index.js</div>

```js
await Window.page.loaded;
// Do stuff which requires page load
```

</div>
<div style="margin-bottom: 60px"></div>

## `reload(ignoreCache = false)`
Reload the page, optionally ignoring the cache (for this reload).

### Arguments

#### Ignore cache
Optionally ignore the cache for this reload. Defaults to false.

### Examples

<div class="glow" style="--glow-hue: 320">
<div class="filename node">index.js</div>

```js
await Window.page.reload(); // Reload the page
await Window.page.reload(true); // Reload the page and ignore the cache
```

</div>
<div style="margin-bottom: 60px"></div>

## `title()`
Get the current title of the page.

### Examples

<div class="glow" style="--glow-hue: 320">
<div class="filename node">index.js</div>

```js
const currentTitle = await Window.page.title();
console.log('Current page title:', currentTitle);
```

</div>
<div style="margin-bottom: 60px"></div>

## `title(newTitle)`
Set the title of the page.

### Arguments

#### New title
The new title to set.

### Examples

<div class="glow" style="--glow-hue: 320">
<div class="filename node">index.js</div>

```js
await Window.page.title('Custom title here');
```

</div>
<div style="margin-bottom: 60px"></div>
