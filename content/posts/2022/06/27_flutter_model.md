---
title: "Flutterでmodelを使う"
date: "2022-06-27"
tags: ["Flutter"]

---

Firestoreから取得したデータを、Wighetの構築に受け渡しするのに引数並べるの大変になってきたので、
modelクラスの導入をしてみた。

参考：
- [【Flutter & FireStore】Modelを作成して、データの一覧を取得 する](https://zenn.dev/ryo_t/articles/5dd6970f2e3f06)
- [【Flutter & FireStore】Modelを作成して、データの一覧を取得・表示する　その２](https://zenn.dev/ryo_t/articles/0a367221d40f11)

無事に引数はまとめることができたのだが、ChangeNotifierProviderを入れたせいなのか描画が2回呼ばれて、どうやら1回目はデータが取れていない状態、2回目はデータが入った状態らしい。

2回呼ばれるのは仕方ないとして、Functionsで取得している内容が、パラメータ変わっているのに同じ内容で返ってきているのが謎。

もしかしたらFunctionsの結果は正しく変化しているのかもしれないけど、表示が1回目（パラメータなし）の状態から変わらないのが良くない。

