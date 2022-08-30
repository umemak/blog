---
title: "MLTファイルを読む"
date: "2022-08-30"
tags: ["go"]

---

MLTをgoのstructに読み込もうとして、やっぱりよくわからない。

MLT自体の仕様は[mltframework/mlt: MLT Multimedia Framework](https://github.com/mltframework/mlt)にある。

xsdファイルがあれば[droyo/go-xml: utility and code-generation libraries for XML](https://github.com/droyo/go-xml)とか使ってgoで使えるようにできそうなんだけど、dtdしかない。

っていうかdtdをstructに書き換えれば良いのか？

と思ったけど良さそうなものが見つかった。[miku/zek: Generate a Go struct from XML.](https://github.com/miku/zek)。
