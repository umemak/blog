---
title: "GoReleaserの代替探し"
date: "2023-03-17"
tags: []

---

ChatGPTに聞いてみた。

- [dep · Dependency management for Go](https://golang.github.io/dep/)
  - 今はgo modに置き換わっている
- [Mage :: Mage](https://magefile.org/)
- [go-task/task: A task runner / simpler Make alternative written in Go](https://github.com/go-task/task)
- [constabulary/gb: gb, the project based build tool for Go](https://github.com/constabulary/gb)
  - メンテナンスされてない

いまいちこれというのがないというか、GoReleaserがそれだけ便利なんだろうな。

そんな中で[Goツールのビルドをおこない、GitHub Releasesにアップロードする | おそらくはそれさえも平凡な日々](https://songmu.jp/riji/entry/2017-10-18-go-tool-release-artifacts.html)という記事を見つけて、やってみようと思う気持ち。

[github actionsによるリリース｜Go言語で複数のシェルスクリプトを実行するcliツールを作ってみた](https://zenn.dev/katsushun89/books/3afdb2bab8f94b/viewer/d3b31e)これも良さそう。
