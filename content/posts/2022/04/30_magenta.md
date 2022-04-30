---
title: "Magenta.js"
date: "2022-04-30"
tags: ["JavaScript"]

---

昨日の[cifkao/html-midi-player: 🎹 Play and display MIDI files on the web](https://github.com/cifkao/html-midi-player)の使い方見ようとして、[magenta-js/music at master · magenta/magenta-js](https://github.com/magenta/magenta-js/tree/master/music/)を使っているのを知った。

Magentaは出始めのときにそんなのがあるのか、って思って深くは見ていなかったのだけど、今度はちゃんと使ってみようかな。

html-midi-playerではSMFファイルを渡して初期化しているところを、
textboxに書かれたマークダウンをSMFに変換して[blobToNoteSequence](https://github.com/magenta/magenta-js/blob/master/music/src/core/midi_io.ts#L274)に渡せばよいのかな。
JavaScriptでテンポラリファイルとか作れるんだっけ・・？それなら無改造で行けそうだけど。
