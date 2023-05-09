---
title: "Rustのエラー"
date: "2023-05-09"
tags: ["rust"]

---

[Amazon.co.jp: Webアプリ開発で学ぶ Rust言語入門 eBook : 佐藤昭文: 本](https://www.amazon.co.jp/gp/product/B0BKK824ZW/)を進めていて、解消できないエラーで詰まる。

149ページから導入される`Validate`でエラー。

```rust
error: cannot find derive macro `Validate` in this scope
  --> src\repositories.rs:31:63
   |
31 | #[derive(Debug, Serialize, Deserialize, Clone, PartialEq, Eq, Validate)]
   |                                                               ^^^^^^^^
   |
note: `Validate` is imported here, but it is only a trait, without a derive macro
  --> src\repositories.rs:8:5
   |
8  | use validator::Validate;
   |     ^^^^^^^^^^^^^^^^^^^
```

全然原因がわからず悩んでいたら、`Cargo.toml`で`features`のスペルが間違っていた。。

Cargo.tomlのlinterないのかな。
