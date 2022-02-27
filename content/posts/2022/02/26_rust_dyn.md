---
title: "dynとは？"
date: "2022-02-26"
tags: ["rust"]

---

[リファクタリングしてモジュール性とエラー処理を向上させる - The Rust Programming Language 日本語版](https://doc.rust-jp.rs/book-ja/ch12-03-improving-error-handling-and-modularity.html#run%E9%96%A2%E6%95%B0%E3%81%8B%E3%82%89%E3%82%A8%E3%83%A9%E3%83%BC%E3%82%92%E8%BF%94%E3%81%99)
を写経していて、コンパイルエラーに遭遇した。

```
$ cargo run
   Compiling mdmml_rust v0.1.0 (mdmml_rust)
error[E0782]: trait objects must include the `dyn` keyword
  --> src/main.rs:21:41
   |
21 | fn run(config: Config)-> Result<(), Box<Error>> {
   |                                         ^^^^^
   |
help: add `dyn` keyword before this trait
   |
21 - fn run(config: Config)-> Result<(), Box<Error>> {
21 + fn run(config: Config)-> Result<(), Box<dyn Error>> {
   | 

For more information about this error, try `rustc --explain E0782`.
error: could not compile `mdmml_rust` due to previous error
```

修正方法も提示してくれて親切。

で、この`dyn`とは何なのか。書かれているように`rustc --explain E0782`を実行すると、以下の出力となった。

```
Trait objects must include the `dyn` keyword.

Erroneous code example:

` ` `
trait Foo {}
fn test(arg: Box<Foo>) {} // error!
` ` `

Trait objects are a way to call methods on types that are not known until
runtime but conform to some trait.

Trait objects should be formed with `Box<dyn Foo>`, but in the code above
`dyn` is left off.

This makes it harder to see that `arg` is a trait object and not a
simply a heap allocated type called `Foo`.

To fix this issue, add `dyn` before the trait name.

` ` `
trait Foo {}
fn test(arg: Box<dyn Foo>) {} // ok!
` ` `

This used to be allowed before edition 2021, but is now an error.
```

Traitオブジェクト（goのinterface{}みたいなもの？）は実行時に型が決まるので、そうであるとコード上明示すべきだと。

で、以前は許されていたが今はエラー扱いになっている、と。

勉強になった。

なお[英語版](https://doc.rust-lang.org/book/ch12-03-improving-error-handling-and-modularity.html#returning-errors-from-the-run-function)は最新の書式に対応されている。
英語版はGitHubへのリンクもあるけど、日本語版ってどこで管理されているんだろう？

[rust-lang-ja/book-ja: Rust文書の和訳レポジトリ](https://github.com/rust-lang-ja/book-ja)
これかな？
