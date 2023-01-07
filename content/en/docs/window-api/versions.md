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

```js
Window.versions.product
// Chrome example: { name: 'Chrome', version: '107.0.5304.107', major: 107 }
// Firefox Nightly example: { name: 'Firefox Nightly', version: '110.0a1', major: 110 }
```

<br>

## `engine`
Version information about the browser engine (Chromium/Firefox) in use. Firefox is referred to as using the "firefox" engine rather than Gecko as forks are based on Firefox directly instead of just Gecko.

### Examples

```js
Window.versions.engine
// Chrome example: { name: 'chromium', version: '107.0.5304.107', major: 107 }
// Firefox Nightly example: { name: 'firefox', version: '110.0a1', major: 110 }
```

<br>

## `jsEngine`
Version information about the browser's JS engine (V8/SpiderMonkey) in use.

{{< alert icon="⚠" text="Firefox incorrectly reports 1.8.5 always as the SpiderMonkey version. <a target=\"_blank\" rel=\"noopener\" href=\"https://bugzilla.mozilla.org/show_bug.cgi?id=1809051\">Relevant bug report</a>." />}}

### Examples

```js
Window.versions.jsEngine
// Chrome example: { name: 'v8', version: '10.7.193.22', major: 10 }
// Firefox Nightly example: { name: 'spidermonkey', version: '1.8.5', major: 1 }
```

<br>
