<div align="center">

  <h1>The Rust and WebAssembly Book</h1>

  <strong>This small book describes how to use Rust and WebAssembly together.  It also consists of tutorials with cool exercises.</strong>

  <h3>
    <a href="https://rust-wasm-wasi.github.io/rust-and-wasm-book/">Read the Book</a>
    <span> | </span>
    <a href="https://github.com/Rust-WASM-WASI/rust-and-wasm-book/blob/main/CONTRIBUTING.md">Contributing</a>
    <span> | </span>
    <a href="https://discordapp.com/channels/442252698964721669/443151097398296587">Chat</a>
  </h3>

  <sub>Built with 🦀🕸 by <a href="https://github.com/Rust-WASM-WASI">The Rust and WebAssembly Working Group & the Rust WASM-WASI contributors </a></sub>
</div>

## About

This repo contains documentation on using Rust for wasm, common workflows, how
to get started and more as you dive deeper. It acts as a guide for doing some really neat things with rust.

If you would like to start learning how to use Rust and WebAssembly together,
 you can read the book [online here][book].

[Open issues for improving the Rust and WebAssembly book.][book-issues]

[For issues on the original book see here.][original-book-issues]

[book-issues]: https://github.com/Rust-WASI-WASI/rustwasm-book/issues

[original-book-issues]: https://github.com/rustwasm/book/issues

## Building the Book

The book is made using [`mdbook`][mdbook]. To install it you'll need `cargo` installed. If you don't have any Rust tooling installed, you'll need to install [`rustup`][rustup] first. Follow the instructions on the site in order to get
set up.

Once you have that done then just do the following:

```bash
$ cargo install mdbook
```

Make sure the `cargo install` directory is in your `$PATH` so that you can run
the mdbook binary.

Now just run this command from root directory of your local git clone of the book:

```bash
$ mdbook serve
```

This will serve the book locally on the `localhost:3000` port for you to read in your web browser. 

If you wish to contribute fixes or changes to this book, running `mdbook serve` in your terminal will automatically generate and serve the files as you make changes.

Alternatively, the files are all written in Markdown so if you don't want to generate the book
to read them, then you can open the *.md files in the `src` directory.

[mdbook]: https://github.com/rust-lang-nursery/mdBook
[rustup]: https://github.com/rust-lang-nursery/rustup.rs/
[book]: https://rust-wasm-wasi.github.io/rust-and-wasm-book/game-of-life/introduction.html
