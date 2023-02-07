---
title: "Open Window"
description: "Open a Gluon window."
lead: "Open a Gluon window."
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "gluon api"
weight: 200
toc: true
---

`Gluon.open` allows you to easily open a new Gluon window.

## Arguments

### URL

The main argument to open is the URL of the website to open the window with.

### Options

There are extra optional options you can use when opening a window, provided as an object:
- `onLoad` - a function to evaluate in the website once it's loaded
- `forceBrowser` - force Gluon to use the provided browser instead of automatically finding and using one (not recommended), use `chrome`/`edge`/`firefox`/`firefox_nightly`/etc
- `forceEngine` - force Gluon to only use the provided browser engine (`chromium`/`firefox`)
- `windowSize` - size of the window to open as `[width, height]`
- `allowHTTP` - opt-in to allowing HTTP (completely disabled by default), options:
  - `false` - HTTP is completely disabled (default)
  - `mixed` - Allow mixed content (but not as the window URL itself). Not recommended.
  - `true` - HTTP is completely allowed. Not recommended.
- `allowRedirects` - choose what redirects should be allowed (not ignored), options:
  - `false` - No redirects are allowed
  - `same-origin` - Only redirects to the same origin are allowed (default)
  - `true` - All redirects are allowed. Not recommended.

## Examples

Open a new Gluon window, loading `https://gluonjs.org`:

```js
import * as Gluon from '@gluon-framework/gluon';

const Window = await Gluon.open('https://gluonjs.org');
```

Open a new Gluon window, loading `https://gluonjs.org` and displaying an alert once loaded:

```js
import * as Gluon from '@gluon-framework/gluon';

const Window = await Gluon.open('https://gluonjs.org', {
  onLoad: () => alert('Hello from Node onLoad!')
});
```

Open a new Gluon window using Chrome Canary, loading `https://gluonjs.org`:

```js
import * as Gluon from '@gluon-framework/gluon';

const Window = await Gluon.open('https://gluonjs.org', {
  forceBrowser: 'chrome_canary'
});
```
