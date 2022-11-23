---
title: "encoding/xml"
date: "2022-11-23"
tags: ["RSS"]

---

`encoding/xml`を使って複数RSS読み込んでマージして出力するのはできたけど、読み込むRSSの形式によって`encoding/xml`では読めないものが出てきた。

やっぱり[mmcdole/gofeed: Parse RSS, Atom and JSON feeds in Go](https://github.com/mmcdole/gofeed)とか形式の違いを吸収してくれるライブラリを利用したほうが良さそう。

作ってみてわかることもある。
