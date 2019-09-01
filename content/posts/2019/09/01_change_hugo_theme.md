---
title: "hugoのテーマを変えてみる"
date: "2019-09-01"
tags: ["hugo"]
---

* [Hermit](https://themes.gohugo.io/hermit/)から[Inkblotty](https://themes.gohugo.io/inkblotty/)へ。
* ちょっと使い勝手が合わないところがあったので[fork](https://github.com/umemak/inkblotty)して改造。

## 変更したところ
* カテゴリとアーカイブ使ってないのにサイドバーに表示されているのを非表示に

## ハマったところ
* 最近の投稿が表示されないのは`postSections`パラメータが違っていた
* config.toml で設定したら表示された
