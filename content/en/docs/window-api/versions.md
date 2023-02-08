---
title: "Versions"
description: ""
lead: ""
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "gluon api"
weight: 308
toc: true
---

## VersionInfo
Versions includes several keys for different parts of the browser you can get information on. Each value is an object containing:
- `name`: Name (Chrome, Chromium, Firefox, etc)
- `version`: Raw version as a string given by the browser
- `major`: Major (x.) version as a number for easy checking

## `product`
Version information about the product (browser) in use.

### Examples

<div class="glow" style="--glow-hue: 320">
<div class="filename node">index.js</div>

```js
Window.versions.product
// Chrome example: { name: 'Chrome', version: '107.0.5304.107', major: 107 }
// Firefox Nightly example: { name: 'Firefox Nightly', version: '110.0a1', major: 110 }
```

</div>
<div style="margin-bottom: 60px"></div>s

## `engine`
Version information about the browser engine (Chromium/Firefox) in use. Firefox is referred to as using the "firefox" engine rather than Gecko as forks are based on Firefox directly instead of just Gecko.

### Examples

<div class="glow" style="--glow-hue: 320">
<div class="filename node">index.js</div>

```js
Window.versions.engine
// Chrome example: { name: 'chromium', version: '107.0.5304.107', major: 107 }
// Firefox Nightly example: { name: 'firefox', version: '110.0a1', major: 110 }
```

</div>
<div style="margin-bottom: 60px"></div>

## `jsEngine`
Version information about the browser's JS engine (V8/SpiderMonkey) in use.

### Examples

<div class="glow" style="--glow-hue: 320">
<div class="filename node">index.js</div>

```js
Window.versions.jsEngine
// Chrome example: { name: 'v8', version: '10.7.193.22', major: 10 }
// Firefox Nightly example: { name: 'spidermonkey', version: '1.8.5', major: 1 }
```

</div>
<div style="margin-bottom: 60px"></div>s
