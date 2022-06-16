---
title: "Flutterでファイルアップロード"
date: "2022-06-16"
tags: ["Flutter"]

---

画像を選択してアップロードする機能を付けたい。

アップロード先はFirebase Storageで。

[Flutter×Firebase(CloudStorage)でファイルダウンロードとアップロードを簡単に実現する方法 - Qiita](https://qiita.com/kazutxt/items/de764db4c9ffb2ee935a)

を見て実装してみたところ、`Unsupported operation: Platform._operatingSystem`なエラーが。

Webだと対応していない書き方なのかな・・環境ごとに分けるの面倒だな・・
