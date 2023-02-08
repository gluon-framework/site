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

IPC (Inter-Process Communication) is how your Node backend and Web frontend communicate with each other. There are 3 "sub-APIs" in IPC you can use:

## Expose Functions

You can easily directly "expose" Node functions to the Web frontend, with a simple wrapper around IPC events built-in. Exposed functions are always async (due to using IPC internally).

<div class="glow" style="--glow-hue: 320">
<div class="filename node">index.js</div>

```js
import * as Gluon from '@gluon-framework/gluon';
const Window = await Gluon.open('https://gluonjs.org');

// Expose our own function to write messages to a log file
import { writeFile } from 'fs/promises';

let log = '';
Window.ipc.log = async msg => {
  log += msg; // Add to log
  return await writeFile('app.log', log) // Write to log file
    .catch(() => false) // Return false on error
    .then(() => true); // Return true on success
};
```

</div>

<div style="margin-bottom: 40px"></div>

<div class="glow" style="--glow-hue: 220">
<div class="filename site">site.js</div>

```js
// Get the config from the Node backend.
const success = await Gluon.ipc.log('Message!');
success // true
```

</div>

<div style="margin-bottom: 60px"></div>

## Store

Easily store common data between the Node backend and Web frontend in both directions. Values must be JSON serializable, and re-set to update the value.

<div class="glow" style="--glow-hue: 320">
<div class="filename node">index.js</div>

```js
import * as Gluon from '@gluon-framework/gluon';
const Window = await Gluon.open('https://gluonjs.org');

// Store common config in IPC Store
Window.ipc.store.config = {
  env: 'production'
};
```

</div>

<div style="margin-bottom: 40px"></div>

<div class="glow" style="--glow-hue: 220">
<div class="filename site">site.js</div>

```js
// Get the config using IPC Store
const { config } = Gluon.ipc.store;
config.env // 'production'
```

</div>

<div style="margin-bottom: 60px"></div>

## Events

Gluon's IPC uses an asynchronous event-based system which you can also use. **It's recommended you use other sub-APIs where appropriate instead of using Events**, as they are easier to use for specific uses. The same example above would look like this using events instead.

<div class="glow" style="--glow-hue: 320">
<div class="filename node">index.js</div>

```js
import * as Gluon from '@gluon-framework/gluon';
const Window = await Gluon.open('https://gluonjs.org');

// Expose our own function to read a config JSON file.
import { readFile } from 'fs/promises';
Window.ipc.on('get config', async () => JSON.parse(await readFile('config.json', 'utf8')));
```

</div>

<div style="margin-bottom: 40px"></div>

<div class="glow" style="--glow-hue: 220">
<div class="filename site">site.js</div>

```js
// Get the config from the Node backend.
const config = await Gluon.ipc.send('get config');
```

</div>

<div style="margin-bottom: 60px"></div>

## Using in the Web frontend

The IPC API is near-identical in the Web frontend to ease development and simplify code. The main difference is there is no Expose API, instead you can call functions exposed via it by doing `Window.ipc[key]()`.
