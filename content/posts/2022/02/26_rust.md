---
title: "VS CodeのRust用設定"
date: "2022-02-26"
tags: ["rust"]

---

コードフォーマッターが欲しいと思って、プラグインを入れたけれど動かない。

```
Couldn't start client Rust Language Server
---
Rustup not available. Install from https://www.rustup.rs/
```

どうやらツールが足りないようなので、追加でインストールした。

```
$ curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
$ source $HOME/.cargo/env
$ rustup --version
rustup 1.24.3 (ce5817a94 2021-05-31)
info: This is the version for the rustup toolchain manager, not the rustc compiler.
info: The currently active `rustc` version is `rustc 1.59.0 (9d1b2106e 2022-02-23)`
```

それでもエラーが解消しなかったので、OSごと再起動したら反映された。
