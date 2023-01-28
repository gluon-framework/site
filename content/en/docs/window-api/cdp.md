---
title: "CDP"
description: ""
lead: ""
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "gluon api"
weight: 310
toc: true
---

## Chrome DevTools Protocol
CDP (Chrome DevTools Protocol) is a remote debugging protocol for browsers, for Chromium but also partially implemented in some other browsers like Firefox. Gluon uses CDP to control and talk to browsers, and also exposes a CDP API for raw CDP access. **You should not have to use this, if there is something not implemented in Gluon's API you have to use CDP for, please request it**. [See the CDP docs for more info.](https://chromedevtools.github.io/devtools-protocol/)

<br>

## `send(method, params?, useSessionId = true)`
Send a CDP command.

### Arguments

#### Method
Method of CDP command to send.

#### Params
Extra parameters of the CDP command to send.

#### Use Session ID
Whether to use the session id of the page or not, on by default. Set false for browser-level commands.
