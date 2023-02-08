---
title: "Security"
description: "A deep dive into Gluon's security."
lead: "A deep dive into Gluon's security."
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

**Gluon is one of the most secure frameworks of its kind.** This is mostly because:
- The browser/web process is **process isolated and sandboxed** from the JS backend, **always**.
- There is **no way to simply expose NodeJS**, or *potentially dangerous* native APIs to the web at all (built-in), and doing anything of the sort is highly discouraged and warned against.
- **HTTP is completely disabled** by default
- **Redirects to other origins are disabled** by default

Any options reducing security are actively warned against in terminal and documentation.

<br>

#### ❌ Dangerous example

**Using IPC this way is dangerous** as it allows the web frontend to make arbitary file reads. Even if you control your website entirely, you still should never really use this approach.

<div class="glow" style="--glow-hue: 320">
<div class="filename node">dangerous_node.js</div>

```js
import * as Gluon from '@gluon-framework/gluon';
const Window = await Gluon.open('https://gluonjs.org');

// Dangerous. Do not do this!
import { readFile } from 'fs/promises';
Window.ipc.expose('readFile', async path => await readFile(path, 'utf8'));
```

</div>

<div style="margin-bottom: 40px"></div>

<div class="glow" style="--glow-hue: 220">
<div class="filename site">dangerous_site.js</div>

```js
// Dangerous. Do not do this!
const config = JSON.parse(await Gluon.ipc.readFile('config.json'));
```

</div>

<div style="margin-bottom: 80px"></div>

#### ✅ Recommended example

Using dedicated exposed functions per task is much safer, as the web frontend can only perform expected operations.

<div class="glow" style="--glow-hue: 320">
<div class="filename node">recommended_node.js</div>

```js
import * as Gluon from '@gluon-framework/gluon';
const Window = await Gluon.open('https://gluonjs.org');

// Not dangerous as FS functions are no longer exposed, much better.
import { readFile } from 'fs/promises';
Window.ipc.getConfig = async () => JSON.parse(await readFile('config.json', 'utf8'));
```

</div>

<div style="margin-bottom: 40px"></div>

<div class="glow" style="--glow-hue: 220">
<div class="filename site">recommended_site.js</div>

```js
// Use dedicated exposed function.
const config = await Gluon.ipc.getConfig();
```

</div>
