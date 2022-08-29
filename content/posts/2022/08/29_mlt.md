---
title: "MLTファイル生成"
date: "2022-08-29"
tags: ["go"]

---

機能追加していたら、ダメなコードの見本みたいになり始めてきた。

機能ごとに分けるとかし始める必要がありそう。

あと、XMLの出力をベタに文字列結合でやっているので、ちゃんとライブラリ使って生成するようにしたい。

Goだと[xml package - encoding/xml - Go Packages](https://pkg.go.dev/encoding/xml)のMarshalを使えば良さそうだけど、構造体の定義面倒だな。。
