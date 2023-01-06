---
title: "Process Model"
description: "A deep dive into Gluon's process model."
lead: "A deep dive into Gluon's process model."
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "gluon-explained"
weight: 100
toc: true
---

### Overview

Gluon's process model is simple:
- Node backend (Node script/app managing the Window)
- Web frontend (browser window)

Compared to Electron's process model, Gluon is simpler as it skips having a preload. This simplifies learning and the development process, plus leads to more efficient resource usage, by not having to use 2 IPC layers.


### Security

Unlike other frameworks, Gluon has no built-in options to directly expose Node or potentially dangerous native APIs to the web frontend. This is intentional to avoid the many security implications which derive from that approach, even if discouraged by the framework.

Gluon's documentation will strongly encourage exposing developer's own functions rather than expose potentially dangerous APIs themselves (like filesystem access).

#### Dangerous example

Using IPC this way is dangerous as it allows the web frontend to make arbitary file reads.

<div class="glow" style="--glow-hue: 320">
<div class="filename">dangerous_node.js</div>

```js
// In your Node backend
import * as Gluon from '@gluon-framework/gluon';
const Window = await Gluon.open('https://gluonjs.org');

// Dangerous. Do not do this!
import { readFile } from 'fs/promises';
Window.ipc.expose('readFile', async path => await readFile(path, 'utf8'));
```

</div>

<div style="margin-bottom: 40px"></div>

<div class="glow" style="--glow-hue: 220">
<div class="filename">dangerous_site.js</div>

```js
// In your website's JS

// Dangerous. Do not do this!
const config = JSON.parse(await Gluon.ipc.readFile('config.json'));
```

</div>

<div style="margin-bottom: 80px"></div>

#### Recommended example

Using dedicated exposed functions per task is much safer as the web frontend can only perform expected/planned operations.

<div class="glow" style="--glow-hue: 320">
<div class="filename">recommended_node.js</div>

```js
// In your Node backend
import * as Gluon from '@gluon-framework/gluon';
const Window = await Gluon.open('https://gluonjs.org');

// Not dangerous as FS functions are no longer exposed, much better.
import { readFile } from 'fs/promises';
Window.ipc.expose('getConfig', async () => JSON.parse(await readFile('config.json', 'utf8')));
```

</div>

<div style="margin-bottom: 40px"></div>

<div class="glow" style="--glow-hue: 220">
<div class="filename">recommended_site.js</div>

```js
// In your website's JS

// Use dedicated exposed function.
const config = await Gluon.ipc.getConfig();
```

</div>