---
title: "Rust再入門"
date: "2022-02-23"
tags: ["rust"]

---

[以前](https://umemak.github.io/blog/posts/2020/08/01_hello_rust/)RustでHello Worldするのはやってたので、再入門。

[The Rust Programming Language 日本語版 - The Rust Programming Language 日本語版](https://doc.rust-jp.rs/book-ja/title-page.html)を見ながら。


今回はcargoを使ってビルドするようにしてみた。

マニュアルだと`cargo new`で作成しているが、先にGitHubでリポジトリを作ってしまっていたので、`cargo init`を使っている。
```
$ curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh
$ source $HOME/.cargo/env
$ rustc --version
rustc 1.58.1 (db9d1b20b 2022-01-20)
$ cargo --version
cargo 1.58.0 (f01b232bc 2022-01-19)
$ cargo init
$ cargo build
   Compiling mdmml_rust v0.1.0 (/home/umemak/workspace/mdmml_rust)
    Finished dev [unoptimized + debuginfo] target(s) in 0.36s
$ ./target/debug/mdmml_rust 
Hello, world!
$ cargo run
    Finished dev [unoptimized + debuginfo] target(s) in 0.00s
     Running `target/debug/mdmml_rust`
Hello, world!
```
