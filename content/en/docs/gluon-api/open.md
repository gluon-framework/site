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

{{< alert icon="🚧" text="These docs are under construction." />}}

`Gluon.open` allows you to easily open a new Gluon window.

## Arguments

### URL

The main argument to open is the URL of the website to open the window with.

### Options

There are extra optional options you can use when opening a window, provided as an object:
- `onLoad` - a function to evaluate in the website once it's loaded
- `forceBrowser` - force Gluon to use the provided browser instead of automatically finding and using one (not recommended)


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
