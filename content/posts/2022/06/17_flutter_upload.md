---
title: "アップロードしたファイルを表示する"
date: "2022-06-17"
tags: ["Flutter"]

---

ファイルを選択してFirebase Storageにアップロードする処理は昨日できた。

フォーム画面で選択したファイルを、アップロードする前にプレビュー表示をしたい。

画像の表示は[Image class - widgets library - Dart API](https://api.flutter.dev/flutter/widgets/Image-class.html)を使えばできる、のだけれど、画面を表示したタイミングではまだ画像が選択されていないので何も表示できない。

画像を選択したら描画されるようにしたい。

providerとか使って状態管理する必要がある？
