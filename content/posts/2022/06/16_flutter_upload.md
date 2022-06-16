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

[google cloud functions - Flutter web - Upload Image File to Firebase Storage - Stack Overflow](https://stackoverflow.com/questions/59716944/flutter-web-upload-image-file-to-firebase-storage)

を見て再チャレンジして、何とかアップロードできた。

`dart:io`ではなく`dart:html`を使い、`putFile`を使わずに`putData`を使うように変えた。

あとFirebase Storageのデフォルト設定が書き込み禁止なので、`allow read, write: if request.auth != null;`として書き込めるように変更した。

- [基本的なセキュリティ ルール  |  Firebase Documentation](https://firebase.google.com/docs/rules/basics?authuser=0&hl=ja#cloud-storage)

何日もハマらずに済んでよかった。
