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
Evaluate JS in the Web frontend and return the result.

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

## `title = newTitle`
Set the current title of the page.

### Examples

```js
Window.page.title = 'Custom title here';
```

## `title`
Get the current title of the page.

### Examples
```js
const currentTitle = Window.page.title;
console.log('Current page title:', currentTitle);
```