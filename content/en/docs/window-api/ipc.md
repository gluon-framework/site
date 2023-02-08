---
title: "IPC"
description: ""
lead: ""
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "gluon api"
weight: 301
toc: true
---

{{< alert icon="ℹ" text="<a href=\"/docs/gluon-explained/ipc/\">See the IPC page in Gluon Explained first for a rundown on what IPC is and does.</a>" />}}

## `ipc[key] = functionToExpose`
Setter to expose a Node function to the Web frontend with a key and handler function.

### Arguments

#### Key
Key to expose as in the Gluon IPC object (`Gluon.ipc[key]`).

#### Function to expose
Function to execute when the exposed function (`Gluon.ipc[key]`) is ran, passed with called args and return value given back to the Web frontend.

### Examples

<div class="glow" style="--glow-hue: 320">
<div class="filename node">index.js</div>

```js
Window.ipc.myFunction = (...args) => {
  console.log('myFunction called!', 'with arguments:', args);
  return 'return value!';
};
```

</div>
<div style="margin-bottom: 60px"></div>s

## `ipc.expose(key, handler)`
Function to expose a Node function to the Web frontend with a key and handler function.

### Arguments

#### Key
Key to expose as in the Gluon IPC object (`Gluon.ipc[key]`).

#### Handler
Function to execute when the exposed function (`Gluon.ipc[key]`) is ran, passed with called args and return value given back to the Web frontend.

### Examples

<div class="glow" style="--glow-hue: 320">
<div class="filename node">index.js</div>

```js
Window.ipc.expose('myFunction', (...args) => {
  console.log('myFunction called!', 'with arguments:', args);
  return 'return value!';
});
```

</div>
<div style="margin-bottom: 60px"></div>

## `ipc.expose(object)`
Function to expose a Node function to the Web frontend with an object instead, allowing multiple functions to be exposed in one call.

### Arguments

#### Object
Object with functions to exposed using keys set in the object.`) is ran, passed with called args and return value given back to the Web frontend.

### Examples

<div class="glow" style="--glow-hue: 320">
<div class="filename node">index.js</div>

```js
Window.ipc.expose({
  myFunction: (...args) => {
    console.log('myFunction called!', 'with arguments:', args);
    return 'return value!';
  },

  functionTheSecond: () => 'wow look, another function!'
});
```

</div>
<div style="margin-bottom: 60px"></div>

## `ipc.on(type, callback)`
Add an IPC listener with a given IPC type from the Web frontend, and run the given callback with data when the type is received.

### Arguments

#### Type
Type of IPC event to listen to (string).

#### Callback
Callback function to run with IPC data when the type is received.

### Examples

<div class="glow" style="--glow-hue: 320">
<div class="filename node">index.js</div>

```js
Window.ipc.on('my type', data => {
  console.log('my type was sent from web with data:', data);
  return { reply: 'here' };
});
```

</div>
<div style="margin-bottom: 60px"></div>

## `ipc.send(type, data?)`
Send a given IPC type and data to the Web frontend.

### Arguments

#### Type
Type of IPC event to send.

#### Data
Data to send with the IPC event. Optional.

### Examples

<div class="glow" style="--glow-hue: 320">
<div class="filename node">index.js</div>

```js
Window.ipc.send('another type', { hey: 'look', some: 'data!' });
```

</div>
<div style="margin-bottom: 60px"></div>

## `delete ipc[key]`
Delete property handler to unexpose (remove) a function with a given key from the Web frontend.

### Arguments

#### Key
Key of the function to unexpose.

### Examples

<div class="glow" style="--glow-hue: 320">
<div class="filename node">index.js</div>

```js
delete Window.ipc.myFunction;
```

</div>
<div style="margin-bottom: 60px"></div>

## `ipc.unexpose(key)`
Function to unexpose (remove) a function with a given key from the Web frontend.

### Arguments

#### Key
Key of the function to unexpose.

### Examples

<div class="glow" style="--glow-hue: 320">
<div class="filename node">index.js</div>

```js
Window.ipc.unexpose('myFunction');
```

</div>
<div style="margin-bottom: 60px"></div>

## `ipc.removeListener(type, callback)`
Remove an IPC listener given the type and callback.

### Arguments

#### Type
Type of IPC event to stop listening to for the callback given.

#### Callback
Callback to stop use of for the IPC event given.

### Examples

<div class="glow" style="--glow-hue: 320">
<div class="filename node">index.js</div>

```js
Window.ipc.removeListener('my type', data => {
  console.log('my type was sent from web with data:', data);
  return { reply: 'here' };
});
```

</div>
<div style="margin-bottom: 60px"></div>s
