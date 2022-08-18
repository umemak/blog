---
title: "wavesurfer.js"
date: "2022-08-18"
tags: ["js"]

---

[wavesurfer.js](https://wavesurfer-js.org/)使ったら、[VTT](https://developer.mozilla.org/ja/docs/Web/API/WebVTT_API)の編集とか直感的にできないかなー、と構想。

[Regions plugin](https://wavesurfer-js.org/plugins/regions.html)と組み合わせれば、波形見ながら開始と終了が指定できて便利だと思うんだ。

VTTファイル読み込んで、パースして配列作ってRegionsと紐づけて、相互に変更が反映されて、VTTファイルとして保存できる機能。

音声ファイルの読み込みも必要か。

動画も同期してプレビュー出来たらもっと良いけど、必須機能ではないな。

