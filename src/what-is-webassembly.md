# What is WebAssembly?

WebAssembly (wasm) is a simple machine model and executable format with an [extensive specification]. 
It is designed to be portable, compact, and execute at or near native speeds.

As a programming language, WebAssembly is comprised of two formats that represent the same structures, albeit in different ways:

1. The `.wat` text format (called `wat` for "**W**eb**A**ssembly **T**ext") uses [S-expressions], and bears some resemblance to the Lisp family of languages
   like Scheme and Clojure.

2. The `.wasm` binary format is lower-level and intended for consumption directly by wasm virtual machines.
   It is conceptually similar to ELF and Mach-O.

For reference, here is a factorial function in `wat`:

```
(module
  (func $fac (param f64) (result f64)
    local.get 0
    f64.const 1
    f64.lt
    if (result f64)
      f64.const 1
    else
      local.get 0
      local.get 0
      f64.const 1
      f64.sub
      call $fac
      f64.mul
    end)
  (export "fac" (func $fac)))
```

If you're curious about what a `wasm` file looks like you can use the [wat2wasm demo] with the above code.

## Linear Memory

WebAssembly has a very simple [memory model]. A wasm module has access to a single "linear memory", which is essentially a flat array of bytes. 
This [memory can be grown] by a multiple of the page size (64K). 
It cannot be shrunk.

## Is WebAssembly Just for the Web?

Although it has currently gathered attention in the JavaScript and Web communities in general, wasm makes no assumptions about its host
environment. 
WASM is a "portable executable" format that is currently being expanded to work in a variety of contexts through [the WebAssembly System Interface (WASI) specification being developed by a sub-group of the WebAssembly CG][wasi-group]. 
For more information about the work happening on the WASI specification, [start here][wasi].


As of *today*, however, WASM is primarily used in one of two ways:
1) as a way to speed up compute-intensive parts of JavaScript (JS) applications, for instance by creating WASM modules to use on the client-side Web, in [NodeJS][Node.js], Deno, or other JS runtimes, or
2) as a way of building fully WASM-based applications using frameworks that compile to `*.wasm`, such as [Leptos][leptos], [Dioxus][dioxus], or [Yew][yew] which are all written in Rust.

This guide will focus primarily on writing WASM for client-side web apps, using both JS and Rust-based WASM frameworks. 

<br/>

If you wish to learn more about WASI and server-side uses of WebAssembly, we recommend visiting [the ByteCode Alliances's][bytecode-alliance] ["WasmTime" project website][wasmtime], which is where the development of the WASI specification is ongoing.
You can read the [WasmTime book here][wasmtime-book].


[memory model]: https://webassembly.github.io/spec/core/syntax/modules.html#syntax-mem
[memory can be grown]: https://webassembly.github.io/spec/core/syntax/instructions.html#syntax-instr-memory
[extensive specification]: https://webassembly.github.io/spec/
[value types]: https://webassembly.github.io/spec/core/syntax/types.html#value-types
[S-expressions]: https://en.wikipedia.org/wiki/S-expression

[wat2wasm demo]: https://webassembly.github.io/wabt/demo/wat2wasm/

[wasi-group]: https://github.com/WebAssembly/WASI/blob/main/Charter.md
[wasi]: https://wasi.dev

[Node.js]: https://nodejs.org
[leptos]: https://leptos.dev
[dioxus]: https://dioxuslabs.com
[yew]: https://yew.rs

[bytecode-alliance]: https://bytecodealliance.org/
[wasmtime]: https://wasmtime.dev
[wasmtime-book]: https://docs.wasmtime.dev
