# @dot-event/wait

[dot-event](https://github.com/dot-event/dot-event#readme) async wait

![wait](wait.gif)

## Install

```bash
npm install dot-event @dot-event/wait
```

## Setup

```js
const dot = require("dot-event")()
require("@dot-event/wait")(dot)
```

## Usage

Wait for two async processes to call `dot.wait`:

```js
async function test() {
  await dot.wait({ count: 2 })
}

await test() // never finishes

await Promise.all([test(), test()]) // finishes
```

## Why?

Sometimes you want to call the same function multiple times asynchronously, and you want each call to wait for certain "checkpoints" across all calls.

As long as you know how many total calls there are (`count`), you can wait for each call to reach `dot.wait` before continuing.

Each `dot.wait` must receive a unique prop to begin a new counter.
