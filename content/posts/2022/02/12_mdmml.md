---
title: "ライブラリの力を借りる"
date: "2022-02-12"

---

機能を追加していってだんだんマークダウンのパターンマッチが面倒になってきたので、パーサー使おうかと。

マークダウンのパーサーは[yuin/goldmark: A markdown parser written in Go. Easy to extend, standard(CommonMark) compliant, well structured.](https://github.com/yuin/goldmark)が良さそう。

で、HTMLに変換したのを[PuerkitoBio/goquery: A little like that j-thing, only in Go.](https://github.com/PuerkitoBio/goquery)で必要な部分を取り出せばよいのでは？という目論見。


