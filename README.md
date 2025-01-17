# BitBox02 Rust and TypeScript library

The APIs of these libraries are currenly highly unstable. Expect frequent breaking changes until
version 1.0.0.

This repo contains both a BitBox02 client library for Rust and for TypeScript. The latter is
produced from the Rust code using [Rust WASM](https://rustwasm.github.io/docs/book/).

The TypeScript library is experimental. Over time, it might replace the [bitbox02-api NPM
package](https://www.npmjs.com/package/bitbox02-api).

# Rust

Install the protoc protobuf compiler, e.g. on Ubuntu:

    sudo apt-get install protobuf-compiler

Check out [examples/connect.rs](examples/connect.rs) for an example.

To run the example:

    cargo run --example connect --features=usb,tokio/rt,tokio/macros

See Cargo.toml or the Makefile for further examples.

To see the library docs:

    cargo doc --open

# TypeScript

Install wasm-pack using:

    cargo install wasm-pack

Install clang so libsecp256k1 can be cross compiled, e.g. on Ubuntu:

    sudo apt-get install clang

The Rust library can be compiled to WASM package including TypeScript definitions using:

    make wasm

The output of this compilation will be in `./pkg`, which is a NPM package ready to be used.

The [sandbox](sandbox/) subfolder contains a React project showcasing the TypeScript API. It
has the library in `./pkg` as a dependency.

The main entry point of the sandbox is at [./sandbox/src/App.tsx](./sandbox/src/App.tsx).

The full package API is described by the TypeScript definitions file `./pkg/bitbox_api.d.ts`.

Run the sandbox using:

    make run-sandbox

Hot-reloading is supported - you can recompile the WASM or change the sandbox files without
restarting the server.
