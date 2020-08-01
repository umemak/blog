---
title: "Rust入門"
date: "2020-08-01"
tags: ["rust"]
---

[なぜDiscordはGoからRustへ移行するのか - MISONLN41's Blog](https://misonln41.hateblo.jp/entry/2020/02/12/232853) を読んで興味がわいたのでインストールしてみた。

[Rust をインストール - Rustプログラミング言語](https://www.rust-lang.org/ja/tools/install) のWSLのコマンドで。インストール完了後、WSLログインしなおさないと`rustc`コマンド使えなかった。

```
$ rustc --version
rustc 1.45.1 (c367798cf 2020-07-26)
```

ファイル作って
```
$ vim hello.rust
fn main() {
    println!("Hello, world!");
}
```

コンパイル＆実行
```
$ rustc hello.rust
$ ./hello
Hello, world!
```
できた。
