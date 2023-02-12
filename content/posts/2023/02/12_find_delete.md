---
title: "空ファイルを削除するコマンド"
date: "2023-02-12"
tags: []

---

空ファイルや空ディレクトリをまとめて削除したいときは`find`でいける。

```sh
$ find . -empty -delete
```

これでカレントディレクトリ配下の空ファイルおよび空ディレクトリが削除できる。

ファイルだけとかディレクトリだけに絞りたいときは、`-type`を指定する。

```sh
$ find . -type d -empty -delete
$ find . -type f -empty -delete
```

削除しないで対象だけ見たいときは、`-delete`の代わりに`-print`を指定する。

参考：
- [Linuxで0バイトのファイル(空ファイル)や空のディレクトリを一括削除する | 俺的備忘録 〜なんかいろいろ〜](https://orebibou.com/ja/home/201606/20160627_002/)
- [空のディレクトリを削除するには - Qiita](https://qiita.com/suzuki-navi/items/075ea29cdf481b711d0a)

