---
title: "WSL2にLAN内のAndroidから接続したい"
date: "2022-06-05"
tags: ["wsl2"]

---

[WSL2で開発中のWebアプリを同じLANのスマホで動作確認する方法](https://zenn.dev/solufa/articles/accessing-wsl2-from-mobile)

ExpoじゃなくてFlutterだけど、上記ページの方法で接続することができた。
まるでここ数日の苦労を見ていたかのようなタイミングでの投稿に感謝。

`New-NetFireWallRule`が重要っぽい。
