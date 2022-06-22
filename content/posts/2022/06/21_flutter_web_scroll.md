---
title: "Firestore Webをスマホで表示したらスクロールできなかった"
date: "2022-06-22"
tags: ["Flutter"]

---

基本的な実装ができたので、Firebase HostingにデプロイしてPixel4で表示してみた。

画像をアップロードして画面の表示項目が増えたら、画面下部のボタンが画面外に出て押せなくなってしまった。

[SingleChildScrollView](https://api.flutter.dev/flutter/widgets/SingleChildScrollView-class.html) でまるっと囲んでしまえば良いらしい。

PWAとしてインストールしていた場合は、再インストールしないと修正が反映されない。
