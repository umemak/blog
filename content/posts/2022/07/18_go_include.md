---
title: "Goのtemplateのinclude"
date: "2022-07-18"
tags: ["go"]

---

テンプレートのincludeってどうやるんだっけ、と思って検索した。

- [Go の html/template でヘッダーやフッター等の共通化を実現する方法 · Yutaka 🍊 Kato](https://mikan.github.io/2019/12/08/implementing-header-and-footer-with-golang-html-template/)

なるほど、`{{define "header"}}`～`{{end}}`で定義して、`{{template "header" .}}`で呼び出すのか。
