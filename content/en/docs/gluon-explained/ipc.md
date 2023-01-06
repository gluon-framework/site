---
title: "IPC"
description: "A deep dive into Gluon's IPC."
lead: "A deep dive into Gluon's IPC."
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "gluon-explained"
weight: 1
toc: true
---

IPC (Inter-Process Communication) is how your Node backend and Web frontend communicate with each other. There are 2 approaches to IPC you can use:

## Expose Functions <small>(Recommended)</small>

You can easily directly "expose" Node functions to the Web frontend, with a simple wrapper around IPC events built-in. This approach is recommended as it's easier to use and work with than having to deal with event listeners, etc.

<div class="glow" style="--glow-hue: 320">
<div class="filename">node.js</div>

```js
// In your Node backend
import * as Gluon from '@gluon-framework/gluon';
const Window = await Gluon.open('https://gluonjs.org');

// Expose our own function to read a config JSON file.
import { readFile } from 'fs/promises';
Window.ipc.getConfig = async () => JSON.parse(await readFile('config.json', 'utf8'));
```

</div>

<div style="margin-bottom: 40px"></div>

<div class="glow" style="--glow-hue: 220">
<div class="filename">site.js</div>

```js
// In your website's JS

// Get the config from the Node backend.
const config = await Gluon.ipc.getConfig();
```

</div>

<div style="margin-bottom: 60px"></div>

## Events

Gluon's IPC uses an asynchronous event-based system which you can also use. The same example above would look like this using events instead.

<div class="glow" style="--glow-hue: 320">
<div class="filename">node.js</div>

```js
// In your Node backend
import * as Gluon from '@gluon-framework/gluon';
const Window = await Gluon.open('https://gluonjs.org');

// Expose our own function to read a config JSON file.
import { readFile } from 'fs/promises';
Window.ipc.on('get config', async () => JSON.parse(await readFile('config.json', 'utf8')));
```

</div>

<div style="margin-bottom: 40px"></div>

<div class="glow" style="--glow-hue: 220">
<div class="filename">site.js</div>

```js
// In your website's JS

// Get the config from the Node backend.
const config = await Gluon.ipc.send('get config');
```

</div>

<div style="margin-bottom: 60px"></div>

## Using in the Web frontend

The IPC API is near-identical in the Web frontend to ease development and simplify code. The main difference is there is no Expose API, instead you can call functions exposed via it by doing `Window.ipc[key]()`.
