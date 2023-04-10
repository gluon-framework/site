---
title: "V8 Cache"
description: "The V8 Cache Window API (Window.v8Cache)"
lead: ""
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "window api"
weight: 311
toc: true
chrome: true
experimental: true
---

{{< alert icon="<div style=\"--icon-size: 24px\" class=\"icon-experimental\"></div>" text="This API is experimental and may not behave as expected." />}}
{{< alert icon="<div style=\"--icon-size: 24px\" class=\"icon-chrome\"></div>" text="This API is Chromium only." />}}

## V8 Caching

V8 allows extra caching of code compilation to help improve load time of the page. This API allows you to interface with V8's cache by building and loading caches with provided options, or automatically. This API is a work-in-progress and experimental, as it does not consider factors like being up to/out of date, etc. [See this V8 post for some more information on code caching.](https://v8.dev/blog/code-caching-for-devs)

<br>

## `build(options?)`

Build a V8 Cache of the current Gluon Window to a JSON file.

### Arguments

#### Options

By default the build will be as eager as possible. There are extra optional options you can use for building, provided as an object:
- `eager` - Use eager compilation (default: true)
- `includePreload` - Try to include preload scripts in the V8 Cache (default: true)
- `reload` - Reload the page to force script recompilation in order to cache (default: true)
- `path` - Path to save the V8 Cache to, recommended to leave as default (default: `v8Cache.json` in Gluon's browser data)
- `urls` - URLs of scripts to compile (default: automatically generated from current page)

### Examples

<div class="glow" style="--glow-hue: 320">
<div class="filename node">index.js</div>

```js
Window.v8Cache.build();
```

</div>
<div style="margin-bottom: 60px"></div>

## `load(path?)`

Load a V8 Cache from a JSON file (optional). Gluon will automatically try to load a V8 Cache in the default path if it exists.

### Arguments

#### Path
Path of V8 Cache to load, defaults to `v8Cache.json` in Gluon's browser data.

### Examples

<div class="glow" style="--glow-hue: 320">
<div class="filename node">index.js</div>

```js
Window.v8Cache.load();
```

</div>
<div style="margin-bottom: 60px"></div>

## `exists(path)`

Check a V8 Cache JSON file exists.

### Arguments

#### Path
Path of V8 Cache JSON file to check.

### Examples

<div class="glow" style="--glow-hue: 320">
<div class="filename node">index.js</div>

```js
Window.v8Cache.exists('/path/to/v8Cache.json');
```

</div>
<div style="margin-bottom: 60px"></div>
