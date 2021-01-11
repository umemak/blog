---
title: "コマンドラインの設定優先度について調べた"
date: "2021-01-11"
tags: ["programmning"]
---

コマンドラインアプリ起動時の設定をするときに、コマンドライン引数、環境変数、設定ファイルどれを優先するのが一般的なのか気になったのでググった結果のメモ。

https://ayasuda.github.io/pages/note_configuration_order_at_command_line.html

まず設定ファイルを読み、環境変数が設定されていれば上書き、コマンドラインで指定されていればさらに上書き。ということでコマンドライン引数が最優先ということが分かった。

```global.yml
---
hoge: "hoge-g"
fuga: "fuga-g"
piyo: "piyo-g"
hogera: "hogera-g"
```
```local.yml
---
piyo: "piyo-l"
```
```
$ hoge=hoge-e fuga=fuga-e cmd -hoge=hoge-c -c=local.yml
hoge: hoge-c
fuga: fuga-e
piyo: piyo-l
hogera: hogera-g
```
こういうことかな。

これを書くときに、piyoの次って何だったっけとググったら、hogera、hogehogeと続くらしいことが分かった。
https://ja.wikipedia.org/wiki/%E3%83%A1%E3%82%BF%E6%A7%8B%E6%96%87%E5%A4%89%E6%95%B0
もっとたくさん必要な時は、hogefuga系ではなくfoobar系の方が良い。
