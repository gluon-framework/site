---
title : "Gluon"
description: "A framework for creating desktop apps from websites, using system installed browsers and NodeJS"
lead: "Develop desktop apps from websites, using system installed browsers and NodeJS"
date: 2020-10-06T08:47:36+00:00
lastmod: 2020-10-06T08:47:36+00:00
draft: false
images: []
---

<div style="margin-bottom: 60px; clear: both"></div>

<div class="col-lg-8" style="float: left">

## Open Window API

Opening a Window in Gluon is as simple as one function call, with more options available if you need them like window size or loading extra code.

</div>

<div class="col-lg-7" style="float: right">

<div class="glow" style="--glow-hue: 320">
<div class="filename">index.js</div>

```js
import * as Gluon from '@gluon-framework/gluon';

const Window = await Gluon.open('https://example.com');
```

</div>

</div>

<div style="margin-bottom: 48px; clear: both"></div>

<div class="col-lg-8" style="float: left">

## IPC API

IPC (Inter-Process Communication) allows you to communicate between your Node backend and website frontend.

Gluon has an easy but powerful asynchronous IPC API, which is also near-identical in Node and the exposed Gluon web API to allow even easier and quicker development.

</div>

<div class="col-lg-7" style="float: right">

<div class="glow" style="--glow-hue: 320">
<div class="filename">node.js</div>

```js
// In your Node backend
import * as Gluon from '@gluon-framework/gluon';
const Window = await Gluon.open(/* ... */);

Window.ipc.on('my type', data => { // { more: 'data' }
  return { different: 'data', original: data.more };
});
```

</div>

<div class="glow" style="--glow-hue: 220">
<div class="filename">site.js</div>

```js
// In your website's JS
const reply = await Gluon.ipc.send('my type', { more: 'data' });
reply // { different: 'data', original: 'data' }
```

</div>

</div>

<div style="margin-bottom: 48px; clear: both"></div>

<div class="col-lg-8" style="float: left">

## Idle API

The Idle API is a unique feature to Gluon, allowing you to "hibernate" or "sleep" Gluon windows to save system resources.

Hibernation fully kills the browser internally (using ~30MB of memory), whilst sleep uses a screenshot of the page as a placeholder (using ~60MB of memory).

You can either hibernate, sleep, and wake up manually with the API, or use automatic idle management which will hibernate the window when minimized for a chosen period of time, and wake it up when it's focused again for you.

</div>

<div class="col-lg-7" style="float: right">

<div class="glow" style="--glow-hue: 320">
<div class="filename">index.js</div>

```js
// In your Node backend
import * as Gluon from '@gluon-framework/gluon';
const Window = await Gluon.open('https://example.com');

const sleep = sec => new Promise(resolve => setTimeout(resolve, sec * 1000));
await sleep(5); // Wait for the window to fully load

Window.idle.hibernate(); // Hibernate the window
await sleep(5);

Window.idle.wake(); // Wake up the window
await sleep(5);

Window.idle.sleep(); // Put the window to sleep
await sleep(5);

Window.idle.wake(); // Wake it up again
```

</div>

</div>

<div style="margin-bottom: 48px; clear: both"></div>
