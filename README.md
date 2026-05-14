# events

> 日本語のREADMEはこちらです: [README.ja.md](README.ja.md)

A Node.js-compatible `EventEmitter` implementation, provided as an ES module for modern JavaScript environments like Deno, browsers, and Node.js.

## Features

- Implements the standard Node.js `EventEmitter` API (`on`, `emit`, `once`, etc.)
- Pure ES module for native use in Deno, browsers, and Node.js
- Written in TypeScript with zero dependencies
- Includes automatic memory leak warnings for excessive listeners

## Usage

Import the `EventEmitter` class and instantiate it. The API is designed to be a drop-in replacement for the one in Node.js.

```javascript
import EventEmitter from "https://code4fukui.github.io/events/events.js";

const myEmitter = new EventEmitter();

myEmitter.on("event", () => {
  console.log("An event occurred!");
});

myEmitter.once("special", (arg) => {
  console.log(`This will only run once with argument: ${arg}`);
});

myEmitter.emit("event");
//> An event occurred!

myEmitter.emit("special", "data");
//> This will only run once with argument: data

myEmitter.emit("event");
//> An event occurred!

myEmitter.emit("special", "more data");
// This does nothing, as the 'once' listener has been removed.
```

## API

This module implements the standard Node.js `EventEmitter` API. For a complete list of methods like `on`, `emit`, `once`, `removeListener`, `setMaxListeners`, and more, please refer to the [official Node.js EventEmitter documentation](https://nodejs.org/api/events.html#class-eventemitter).

## To Build

This project uses Deno. To bundle the source TypeScript file into a single JavaScript file for distribution, run the following command:

```sh
deno bundle events.ts events.js
```

## License

MIT License — see [LICENSE](LICENSE).