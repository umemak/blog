---
title: "FlutterでGeoChart"
date: "2022-06-10"
tags: ["Flutter"]

---

リクエスト受けてHTML組み立てて返すFirebase Functions作って、これをWebViewXで利用することで実現できた。

[photomap/index.ts at main · umemak/photomap](https://github.com/umemak/photomap/blob/main/functions/src/index.ts)

https://github.com/umemak/photomap/blob/c70f1a41038bd5a82edd72b63971ea83a393b41a/lib/MapDetailPage.dart#L140-L149

[webview_flutter | Flutter Package](https://pub.dev/packages/webview_flutter)はAndroid/iOSしか対応していないみたいなので、あきらめた。
