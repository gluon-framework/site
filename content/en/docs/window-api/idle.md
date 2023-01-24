---
title: "Idle"
description: ""
lead: ""
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "gluon api"
weight: 309
toc: true
---

<script>
document.querySelector('.col-xl-3').classList.add('col-xl-4'); // Make table of contents wider
</script>

{{< alert icon="🧪" text="This API is experimental and may not behave as expected." />}}
{{< alert icon="⚠" text="This API is currently Chromium only." />}}

## `hibernate()`
Put the window into hibernation. Only supported on Windows, will automatically use `sleep()` as a fallback instead on other platforms.

### Examples

```js
Window.idle.hibernate(); // Hibernate the window
```

<br>

## `sleep()`
Put the window to sleep.

### Examples

```js
Window.idle.sleep(); // Put the window to sleep
```

<br>

## `wake()`
Wake up the window from hibernation or sleep.

### Examples

```js
Window.idle.wake(); // Wake up the window
```

<br>

## `auto(enabled, options?)`
Enable/disable automatic idle management (disabled by default), and manage it's options.

### Arguments

#### Enabled
Whether to enable or disable automatic idle management (true/false).

#### Options
Object of options, all optional including Object itself:
- `timeMinimizedToHibernate`: How long the window should be minimized before hibernating, in seconds. Defaults to 10.

### Examples

```js
Window.idle.auto(true); // Enable automatic idle management
Window.idle.auto(false); // Disable automatic idle management

Window.idle.auto(true, { // Enable and change options:
  timeMinimizedToHibernate: 30 // Be minimized for 30s before hibernating automatically
});
```
