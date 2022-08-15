---
title: "Ginkgo難解"
date: "2022-08-15"
tags: ["go"]

---

久しぶりに[onsi/ginkgo: A Modern Testing Framework for Go](https://github.com/onsi/ginkgo)触って、やっぱりよくわからないなー、と。

BeforeEachとか使って、初期化処理を共通化しようとしたのだけれど、初期化されていない現象とか。

テスト用の構造体ってちゃんと作ろうとすると結構行数食ってしまうけど、あまりテストコードと離れたところに置きたくない気持ちもあり。

うーん。
