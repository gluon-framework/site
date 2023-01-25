---
title: "Page"
description: ""
lead: ""
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "gluon api"
weight: 302
toc: true
---

## `eval(expression)`
Evaluate JS in the Web frontend and return the result. If there's an error, it will return it like the window usually would (like `ReferenceError: notDefined is not defined`).

### Arguments

#### Expression
JS to evaluate, either as a function or string.

### Examples

```js
// Get the current url of the document
const currentUrl = await Window.page.eval(`location.href`);
```

<br>

## `loaded`
A Promise which is resolved when the page loads (like `window.onload`).

### Examples

```js
await Window.page.loaded;
// Do stuff which requires page load
```

<br>

## `title()`
Get the current title of the page.

### Examples
```js
const currentTitle = await Window.page.title();
console.log('Current page title:', currentTitle);
```

## `title(newTitle)`
Set the title of the page.

### Arguments

#### New title
The new title to set.

### Examples

```js
await Window.page.title('Custom title here');
```
