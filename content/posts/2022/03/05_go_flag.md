---
title: "コマンドライン引数をflagで処理する"
date: "2022-03-05"
tags: ["go"]

---

入力ファイルを`os.Args[1]`で取得していたので、引数指定しないと範囲外アクセスでpanicしていた。

flagパッケージ使って`flag.Arg(0)`で取得するようにしたので、引数指定しなかった場合にはファイルなしエラーで終わるようになった。

もっと親切にするなら、エラー終了ではなくヘルプ表示にするのが良いのだろうけど、それはまた余裕があるときにでも。