---
title: "Flutter Webのフォント問題"
date: "2022-06-30"
tags: ["Flutter"]

---

Flutter Webでブラウザ表示したときに、漢字が中国風になってしまう件。

`--web-renderer html`で動かせば回避できていたのだけれど、cropを試すのに`--web-renderer canvaskit`にしたら再発した。

[Flutter Webでのフォント問題を解決する](https://zenn.dev/enoiu/articles/596078e878145d)を参考にsawarabiGothicにして解決。

