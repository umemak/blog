---
title: "urfave/cli"
date: "2023-03-25"
tags: ["go"]

---

[Go言語プログラミングエッセンス | Gihyo Digital Publishing](https://gihyo.jp/dp/ebook/2023/978-4-297-13420-4)で紹介されていた、[urfave/cli: A simple, fast, and fun package for building command line apps in Go](https://github.com/urfave/cli)を使ってみたのだけど、エラーで動かない。

`no required module provides package github.com/urfave/cli/v2`というエラー。v1だとエラーは出ない。v2とv3がダメ。

試しにGitpodで動かしてみたら、エラー出なかった。

Windowsの問題？
