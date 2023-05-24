---
title: "Rustのエラー"
date: "2023-05-07"
tags: ["rust"]

---

[Amazon.co.jp: Webアプリ開発で学ぶ Rust言語入門 eBook : 佐藤昭文: 本](https://www.amazon.co.jp/gp/product/B0BKK824ZW/)を進めていて、解消できないエラーで詰まる。

136ページで暫定として入れている、`Ok(StatusCode::OK)`が型の不一致エラー。

コメント通りならあとで取り除くから、いずれは解消するのだろうけど、それまではテストも通らない状態になるのでよくない。

→143ページで実装が入ったが、それでもエラーは解消せず。。。

→サポートレポジトリのコードと見比べたら、書いた記憶のないuseが居て、それを削除したらエラー解消した。つらい。