---
title: "ginkgoとgo test"
date: "2022-04-25"
tags: ["golang", "ginkgo"]

---

GinkgoのV1とV2のテストケースが混在しているときに、V2のCLIでV1用のコードをテストしようとすると、ginkgo.timeoutが定義されてい内的なエラーになってしまう（うろ覚え）。

importをv2にすれば多分良いのだけれど、そうしなくても、テストの実行をgo testに任せれば、importで指定しているバージョンで実行してくれる気がする。

[https://onsi.github.io/ginkgo/](https://onsi.github.io/ginkgo/)によれば、
> Under the hood, ginkgo is simply calling go test.

ということなので、おかしな挙動にはならない・・と思う。

> While you can run go test instead of the ginkgo CLI, Ginkgo has several capabilities that can only be accessed via ginkgo.

特別な機能を使っていない限りは。

