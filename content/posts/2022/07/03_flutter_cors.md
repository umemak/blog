---
title: "FlutterでCORS"
date: "2022-07-03"
tags: ["Flutter"]

---

crop使うために、--web-rendererをcanvaskitにしたら、Firebase Storageの画像を表示できなくなってしまった。

[Displaying images on the web | Flutter](https://docs.flutter.dev/development/platform-integration/web/web-images#cross-origin-images)にも書かれていて、いくつか回避策が提示されていた。

Firebase Hostingはfirebase.jsonで設定できるらしいが、今回問題になっているのはStorageの方で。

[ウェブで Cloud Storage を使用してファイルをダウンロードする  |  Firebase Documentation](https://firebase.google.com/docs/storage/web/download-files?hl=ja#cors_configuration)に書かれているように、gsutilを使って設定する必要があるとのことで、ちょっと面倒。。

gsutilのインストールが面倒だったけど、GCPのCloud Shell使ったら最初からインストールされてたので、cors.json作って実行したら行けた。

Webアプリからも表示できるようになって、解決。

cropはまだできていない。
