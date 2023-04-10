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

<small style="color: #a0a4a8; font-size: 0.6em">Time until FCP. Gluon using Chromium. All frameworks in release config, on Windows 10.</small>
</div>

<div style="margin-bottom: 60px; clear: both"></div>

<div class="col-lg-8" style="float: left">

## Tiny Builds

Gluon has tiny builds thanks to a custom bootstrapper written in Nim, allowing dependencies (like Node) to only be downloaded on the fly when not already installed.

</div>

<div class="col-lg-7" style="float: right">

<div class="chart nopadding">
<span>Build Size <small style="margin-left: 6px; font-size: 0.6em">Windows x64</small></span>
<div>
<span>Gluon <div title="Experimental" class="icon-experimental" style="vertical-align: revert; position: relative; top: 1px; left: 2px; --size: 15px; color: #a0a4a8"></div></span>
<!-- <div class="glow" id="gluon-build-size" style="--glow-hue: 320; width: calc((100% - 140px) * (0.25 / 2.6))"></div> -->
<div class="glow" id="gluon-build-size" style="--glow-hue: 320; width: calc((100% - 140px) * (0.2 / 220))"></div>
</div>
<div>
<span>Tauri</span>
<div id="tauri-build-size" style="width: calc((100% - 140px) * (1.7 / 220))"></div>
</div>
<div>
<span>Neutralinojs</span>
<div id="neutralinojs-build-size" style="width: calc((100% - 140px) * (2.6 / 220))"></div>
</div>
<div>
<span>Electron</span>
<div id="electron-build-size" style="width: calc((100% - 140px) * (220 / 220))"></div>
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

const wait = ms => new Promise(resolve => setTimeout(resolve, ms));
await wait(5000); // Wait for everything to fully load

Window.idle.hibernate(); // Hibernate the window
await wait(5000);

Window.idle.wake(); // Wake up the window
await wait(5000);

Window.idle.sleep(); // Put the window to sleep
await wait(5000);

Window.idle.wake(); // Wake it up again
```

</div>

</div>

<div style="margin-bottom: 48px; clear: both"></div>

<div class="col-lg-7" style="float: left">

## Also featuring...

### Browser Extensions

Gluon also features best-in-class browser extension support:

| Extension Feature | <span style="font-weight: 900; color: #c2a2df">Gluon</span> | <span style="font-weight: 600">Electron</span> | <span style="font-weight: 600">Tauri</span> |
| ---- | :---: | :------: | :---: |
| Extension Support<br><small style="color: #a0a4a8; font-size: 0.8em">Basic browser extension support</small> | 🟢 | 🟢 | 🔴 |
| DevTools Extensions<br><small style="color: #a0a4a8; font-size: 0.8em">DevTools extensions like React DevTools work</small> | 🟢 | 🟢 | 🔴 |
| Manifest V2<br><small style="color: #a0a4a8; font-size: 0.8em">Support for Manifest V2</small> | 🟢 | 🟢 | 🔴 |
| Manifest V3<br><small style="color: #a0a4a8; font-size: 0.8em">Support for Manifest V3 (new format/APIs)</small> | 🟢 | 🔴 | 🔴 |
| WebExtension APIs Support<br><small style="color: #a0a4a8; font-size: 0.8em">Broad support for various WebExtension APIs</small> | 🟢 | 🟡 | 🔴 |

<small style="color: #a0a4a8; font-size: 0.8em; display: flex; gap: 16px">
<span>🟢 Supported</span>
<span>🟡 Partial</span>
<span>🔴 Unsupported</span>
</small>

</div>

<div class="col-lg-7" style="float: right">

## &nbsp;

### Security in Mind

Gluon has strict security, by default, without developer annoyance:

| Extension Feature | <span style="font-weight: 900; color: #c2a2df">Gluon</span> | <span style="font-weight: 600">Electron</span> | <span style="font-weight: 600">Tauri</span> |
| ---- | :---: | :------: | :---: |
| Process Isolation<br><small style="color: #a0a4a8; font-size: 0.8em">Isolate and sandbox processes for enhanced security</small> | 🟢 | 🟢 | 🟢 |
| No localhost Server<br><small style="color: #a0a4a8; font-size: 0.8em">Do not use a localhost server which could be exposed</small> | 🟢 | 🟢 | 🟢 |
| Content Security Policy<br><small style="color: #a0a4a8; font-size: 0.8em">Use a CSP to stop unwanted external content</small> | 🟢 | 🟡 | 🟡 |
| Limited Navigations<br><small style="color: #a0a4a8; font-size: 0.8em">Prevent navigation to untrusted origins</small> | 🟢 | 🟡 | 🔴 |
| HTTPS Only<br><small style="color: #a0a4a8; font-size: 0.8em">Only accept HTTPS URLs and content</small> | 🟢 | 🔴 | 🔴 |

<small style="color: #a0a4a8; font-size: 0.8em; display: flex; gap: 16px">
<span>🟢 Default</span>
<span>🟡 Opt-in</span>
<span>🔴 Unimplemented</span>
</small>

</div>

<div style="margin-bottom: 120px; clear: both"></div>

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
