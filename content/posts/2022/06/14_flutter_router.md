---
title: "Flutterのrouter選定"
date: "2022-06-14"
tags: ["Flutter"]

---

画面レイアウトの調整が面倒な件、ロジックを作り始めると、目的の画面にたどり着くまでに手数が必要になるせいだと気づいた。

ということで、目的の画面に直接アクセスできるように（Webアプリ版なので）URL指定で開けるようにする。

そのためにはrouterを使うのが良さそう。

軽く検索したところ、以下のパッケージがヒットした。

- [vrouter | Flutter Package](https://pub.dev/packages/vrouter/example)
- [fluro | Flutter Package](https://pub.dev/packages/fluro)
- [go_router | Flutter Package](https://pub.dev/packages/go_router)

今回はその中で唯一[Flutter Favorite](https://docs.flutter.dev/development/packages-and-plugins/favorites)がついている、go_routerを使ってみる。

参考にしたページ：
- [Flutterを再開するときにやったこと。その3(go_routerを使ってみる) - くらげになりたい。](https://www.memory-lovers.blog/entry/2022/04/07/173000)
- [go_routerを使ってみた(単純な画面遷移の方法) - Qiita](https://qiita.com/Umigishi-Aoi/items/25ae18293915b017aa4a)

単純に遷移しているところは簡単に置き換えられた。
パラメータを渡すところはよくわからん。

あとログイン周りも理解が追い付いていない。
