---
title: "Introduction"
description: "Gluon is a framework for creating desktop apps from websites, using system installed browsers and NodeJS."
lead: "Gluon is a framework for creating desktop apps from websites, using system installed browsers and NodeJS."
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "guide"
weight: 100
toc: true
---

{{< alert icon="⚠" text="These docs are intended for those already familiar with NodeJS and webdev." />}}

## Why Gluon?

Existing frameworks either bundle Chromium (Electron) or use WebView2/WebKitGTK (Tauri/many others). Instead of doing either of those, Gluon uses normal already installed browsers instead. Rather than just use marketing and vague claims, here are some real pros and cons:


### Advantages over bundling

- Tiny build sizes in comparison
- Chromium version isn't coupled to build
- More freedom/choice for users

### Advantages over WebView2

- Don't have to rely on system installed libraries
- Fully open source (WebView2 is closed source)
- More features supported (browser extensions, etc)
- Don't have to worry about using other libraries on non-Windows
- More freedom/choice for developers and users (not locked into one ecosystem/library/engine)

### Advantages over Webkit2GTK

- Don't have to rely on system installed libraries
- DRM content playback in Chrome/Chromium or Firefox (Webkit2GTK does not support Widevine)

<br>

### Disadvantages over bundling

- Not always sure what you'll work with

### Disadvantages over WebView2

- WebView2 is well supported, maintained, and relatively stable
