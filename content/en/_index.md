---
title : "Gluon"
description: "A framework for creating desktop apps from websites, using system installed browsers and NodeJS."
lead: "Develop desktop apps from websites, using system installed browsers and NodeJS."
date: 2020-10-06T08:47:36+00:00
lastmod: 2020-10-06T08:47:36+00:00
draft: false
images: []
---

<div style="margin-bottom: 60px; clear: both"></div>

<div class="col-lg-10" style="float: left">

## Cross-platform, Cross-browser, Cross-runtime

Gluon supports Windows, Linux, and Mac, with most Chromium-based and Firefox-based browsers supported. You can also use Node, Deno, or Bun as the JS Runtime powering your app (experimental).

</div>

<div class="col-lg-5" style="float: right">

<div class="cross-diagram">
<span>Platforms</span>
<div>
<div class="icon-box" title="Windows"><div class="icon-windows"></div></div>
<div class="icon-box orange" title="Linux"><div class="icon-linux"></div></div>
<div class="icon-box gray" title="Mac"><div class="icon-mac"></div><div title="Experimental" class="icon-experimental"></div></div>
</div>
<span>Runtimes</span>
<div>
<div class="icon-box" title="NodeJS" style="background: rgba(101, 184, 73, 0.37)"><div class="icon-node"></div></div>
<div class="icon-box" title="Deno" style="background: rgba(18, 18, 75, 0.37)"><div class="icon-deno"></div><div title="Experimental" class="icon-experimental"></div></div>
<div class="icon-box" title="Bun" style="background: rgba(251, 240, 223, 0.37)"><div class="icon-bun"></div><div title="Experimental" class="icon-experimental"></div></div>
</div>
<span>Browsers</span>
<div>
<div class="icon-box gray" title="Chromium-based" style="background: rgba(174, 203, 250, 0.37)"><div class="icon-chrome"></div></div>
<div class="icon-box orange" title="Firefox-based" style="background: rgba(255, 67, 63, 0.37)"><div class="icon-firefox"></div><div title="Experimental" class="icon-experimental"></div></div>
<div class="icon-box gray" title="Chromium-based" style="background: transparent"><div class="text-icon">+</div></div>
</div>
</div>

</div>

<div style="margin-bottom: 60px; clear: both"></div>


<div class="col-lg-8" style="float: left">

## Performant

Gluon is not only versatile, but also one of the fastest frameworks out there. By looking into browser internals and using a curated set of flags, Gluon tries to squeeze out the most performance possible whilst also aiming to use less memory and resources.

</div>

<div class="col-lg-7" style="float: right">

<div class="chart">
<span>Startup Time</span>
<div>
<span>Gluon</span>
<div class="glow" style="--glow-hue: 320; width: calc((100% - 140px) * 0.33)">0.4s</div>
</div>
<div>
<span>Electron</span>
<div style="width: calc((100% - 140px) * 0.41)">0.5s</div>
</div>
<div>
<span>Tauri</span>
<div style="width: calc((100% - 140px) * 0.75)">0.9s</div>
</div>
<div>
<span>Neutralinojs</span>
<div style="width: calc((100% - 140px) * 1)">1.2s</div>
</div>
</div>

</div>

<div style="margin-bottom: 60px; clear: both"></div>

<div class="col-lg-8" style="float: left">

## Open Window API

Opening a Window in Gluon is as simple as one function call, with more options available if you need them like window size or loading extra code.

</div>

<div class="col-lg-7" style="float: right">

<div class="glow" style="--glow-hue: 320">
<div class="filename node">index.js</div>

```js
import * as Gluon from '@gluon-framework/gluon';

const Window = await Gluon.open('https://gluonjs.org');
```

</div>

</div>

<div style="margin-bottom: 48px; clear: both"></div>

<div class="col-lg-8" style="float: left">

## IPC API

IPC (Inter-Process Communication) allows you to communicate between your Node backend and website frontend.

Gluon has an easy but powerful asynchronous IPC API, which is also near-identical in Node and the exposed Gluon web API to allow even easier and quicker development.

It also has multiple versatile sub-APIs for doing common things, wrapping the base API so most developers won't need to use a needlessly complex event-based system:

##### Expose
Easily expose Node functions to Web.

##### Store
Share common data effortlessly between Node and Web both ways.

<a href="/docs/gluon-explained/ipc/">Learn more about Gluon's IPC here.</a>

</div>

<div class="col-lg-7" style="float: right">

<div class="glow" style="--glow-hue: 320">
<div class="filename node">index.js</div>

```js
import * as Gluon from '@gluon-framework/gluon';
const Window = await Gluon.open('https://gluonjs.org');

Window.ipc.store.config = {
  env: 'production'
};

import { writeFile } from 'fs/promises';

let log = '';
Window.ipc.log = msg => { // Log data to a log file on disk
  log += msg;
  writeFile('app.log', log); // Write to log file
};
```

</div>

<div class="glow" style="--glow-hue: 220">
<div class="filename site">site.js</div>

```js
// Get data from IPC Store
const { env } = Gluon.ipc.store.config;
env // 'production'

// Call exposed IPC function
Gluon.ipc.log('Stored to log file!');
```

</div>

</div>

<div style="margin-bottom: 48px; clear: both"></div>

<div class="col-lg-8" style="float: left">

{{< changelog-header-h2 "experimental" "Idle API" >}}

The Idle API is a unique feature to Gluon, allowing you to "hibernate" or "sleep" Gluon windows to save system resources.

Hibernation fully kills the browser internally (using ~30MB of memory), whilst sleep uses a screenshot of the page as a placeholder (using ~60MB of memory).

You can either hibernate, sleep, and wake up manually with the API, or use automatic idle management which will hibernate the window when minimized for a chosen period of time, and wake it up when it's focused again for you.

</div>

<div class="col-lg-7" style="float: right">

<div class="glow" style="--glow-hue: 320">
<div class="filename node">index.js</div>

```js
import * as Gluon from '@gluon-framework/gluon';
const Window = await Gluon.open('https://example.com');

const sleep = ms => new Promise(resolve => setTimeout(resolve, ms));
await sleep(5000); // Wait for the window to fully load

Window.idle.hibernate(); // Hibernate the window
await sleep(5000);

Window.idle.wake(); // Wake up the window
await sleep(5000);

Window.idle.sleep(); // Put the window to sleep
await sleep(5000);

Window.idle.wake(); // Wake it up again
```

</div>

</div>

<div style="margin-bottom: 48px; clear: both"></div>

<div class="glow rainbow">

![Screenshot of a Gluon Hello World app showing versions with 2 windows, one using Chrome Canary and another using Firefox Nightly.](/gluon_dual.png)

</div>

<script>
  // swap to smaller image with just one window if small screen
 if (window.innerWidth < 800) {
  document.querySelector('.img-fluid').src = '/gluon_chrome.png';
  document.querySelector('.img-fluid').alt = 'Screenshot of a Gluon Hello World app showing versions, using Chrome.';
 }
</script>

<div style="margin-bottom: 48px; clear: both"></div>
