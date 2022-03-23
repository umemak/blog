---
title: "GAS入門"
date: "2020-05-28"
tags: ["gas"]
---

今まで存在は知っていたし、Kindle Unlimitedで読める入門書を読んだりはしていた。
ここにきてようやく実際に手を動かしてみたので、その感想。

作ったものは、POSTリクエストを受けて、スプレッドシートのA列に入力と同じ文字列があれば、B列の内容を返すというもの。

学び
* スクリプトを修正したときは、Newバージョンでデプロイする。
  - バージョン変えずに更新ボタン押して、なんで挙動変わらないんだろうと悩んだ。
  - デフォルトが`New`でも良いと思うんだけど。。
* `TextFinder`で特定の列から検索するメソッドは（たぶん）用意されていない。
  - `findAll()`で全体から拾って、ループ回して`getColumn()`で列番号を比較して拾う。
* WindowsのVSCodeのターミナルでは、`curl`で日本語をパラメータとして渡すと正しく伝わらない。
  - 文字コードの問題。
  - WSLに入って実行すればOK。
* そんなに速度は速くない。
  - とはいえ遅すぎるというほどでもない。

これでGAS実績が解放された。