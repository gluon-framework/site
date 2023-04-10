---
title: "Idle"
description: "The Idle Window API (Window.idle)"
lead: ""
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "window api"
weight: 309
toc: true
chrome: true
experimental: true
---

{{< alert icon="<div style=\"--icon-size: 24px\" class=\"icon-experimental\"></div>" text="This API is experimental and may not behave as expected." />}}
{{< alert icon="<div style=\"--icon-size: 24px\" class=\"icon-chrome\"></div>" text="This API is currently Chromium only." />}}

## `hibernate()`
Put the window into hibernation. This kills the internal browser processes to save the most resources. The page state is lost (as if refreshed).

### Examples

<div class="glow" style="--glow-hue: 320">
<div class="filename node">index.js</div>

```js
Window.idle.hibernate(); // Hibernate the window
```

</div>
<div style="margin-bottom: 60px"></div>

## `sleep()`
Put the window to sleep. This switches to a screenshot of the window instead of the actual window running. The page state is lost (as if refreshed).

### Examples

<div class="glow" style="--glow-hue: 320">
<div class="filename node">index.js</div>

```js
Window.idle.sleep(); // Put the window to sleep
```

</div>
<div style="margin-bottom: 60px"></div>

## `freeze()`
Freeze the window. Halts most execution and background work. The page state is kept when woken (as if nothing happened). Unfreeze using `wake()`.

### Examples

<div class="glow" style="--glow-hue: 320">
<div class="filename node">index.js</div>

```js
Window.idle.freeze(); // Freeze the window
```

</div>
<div style="margin-bottom: 60px"></div>

## `wake()`
Wake up the window from hibernation or sleep.

### Examples

<div class="glow" style="--glow-hue: 320">
<div class="filename node">index.js</div>

```js
Window.idle.wake(); // Wake up the window
```

</div>
<div style="margin-bottom: 60px"></div>

## `auto(enabled, options?)`
Enable/disable automatic idle management (disabled by default), and manage it's options.

### Arguments

#### Enabled
Whether to enable or disable automatic idle management (true/false).

#### Options
Object of options, all optional including Object itself:
- `timeMinimizedToHibernate`: How long the window should be minimized before hibernating, in seconds. Defaults to 10.

### Examples

<div class="glow" style="--glow-hue: 320">
<div class="filename node">index.js</div>

```js
Window.idle.auto(true); // Enable automatic idle management
Window.idle.auto(false); // Disable automatic idle management

Window.idle.auto(true, { // Enable and change options:
  timeMinimizedToHibernate: 30 // Be minimized for 30s before hibernating automatically
});
```

</div>
<div style="margin-bottom: 60px"></div>
