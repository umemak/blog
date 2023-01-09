---
title: "ASINからMD生成する"
date: "2023-01-09"
tags: ["amazon"]

---

売り上げがなくてPA-APIが使えなかったので、HTMLから抜き出すようにしてみた。

- [umemak/asin2md](https://github.com/umemak/asin2md)

とりあえずKindleのASINから取り出してフロントマターに書き出した。

抽出には[PuerkitoBio/goquery: A little like that j-thing, only in Go.](https://github.com/PuerkitoBio/goquery)を使っている。

Kindle以外はあまり試していないが、うまく取れない商品があることは認識している。

あと、著者のところが謎な構成になっていて、`span.author.notFaded`の直下にある場合と、もう一段`span`が入っている場合があった。
直下にある方を先に処理しているので、ものによってはWebでの見た目の順番と入れ替わってしまう場合がある。
