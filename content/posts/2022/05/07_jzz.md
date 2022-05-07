---
title: "JZZ-gui-Player"
date: "2022-05-07"
tags: ["JavaScript", "midi"]

---

[magenta-js](https://github.com/magenta/magenta-js/tree/master/music)がうまく動いてくれなくて、他に似たもの探して
[jazz-soft/JZZ-gui-Player: MIDI Player for browsers](https://github.com/jazz-soft/JZZ-gui-Player)を使ってみた。

readmeのサンプルの通りだと音が出なかったけど、デモページのソースを参考に`JZZ.synth.Tiny.register('Web Audio');`を追加したらできた。

あとはエディタ部分をマークダウン対応のWYSIWYGなものを組み込めば、いい感じになりそう。
