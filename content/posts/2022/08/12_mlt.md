---
title: "MLTファイルを作る2"
date: "2022-08-12"
tags: ["go", "python"]

---

silencedetectがなんか思ったのと違う感じで、代わりに[Pythonとffmpegで動画の無音部分をカットする - Qiita](https://qiita.com/igapon1/items/3faa83fc8af1543bc672)にあるPythonのプログラムの無音検出部分を使ってみた。

Goでも[mkb218/gosndfile: Go bindings for libsndfile](https://github.com/mkb218/gosndfile)を使ったらできそうだけど、importしただけでは動かなかったので今後の課題にしたい。
