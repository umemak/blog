---
title: "Rust学習"
date: "2022-02-27"
tags: ["rust"]

---

[The Rust Programming Language 日本語版 - The Rust Programming Language 日本語版](https://doc.rust-jp.rs/book-ja/title-page.html)、途中飛ばして12章やってたけれど、やっぱり最初からやったほうが良い気がしてきた。

そして、最初のページに
> すべてのプロジェクトの Cargo.toml に edition="2018" とあることを前提にしています。
との注意書きがあるのに今更ながら気づいた。

昨日エラーが出ると言っていたのは、`edition = "2021"`だったので、試しに2018にしてみたらエラーではなく警告に変わった。
> warning: trait objects without an explicit `dyn` are deprecated

また一つ勉強になった。
