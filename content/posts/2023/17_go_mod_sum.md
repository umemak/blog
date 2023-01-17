---
title: "goでmissing go.sum entry cacheエラー"
date: "2023-01-17"
tags: ["go"]

---

昨日の`go build`でエラーになって`go run`だと動く件、正確にはbuildのほうはmake経由での実行で、runは直接という違いがあった。

goのバージョン管理について、新しいバージョンが出たら[Managing Go installations - The Go Programming Language](https://go.dev/doc/manage-install)のように`go install`を使ってインストールしていて、aliasでインストールした先を`go`としていた。

これが間違い。

make経由だと、goのバイナリは`/usr/local/go/bin/go`を参照していて、コマンドラインだと`~/sdk/go1.19.2/bin/go`を参照していた。

なので、コマンドラインで`go mod tidy`を実行してもmakeで実行するほうのモジュールは更新されなかったというオチ。

`go install`でインストールするときは、一時的な使用に限るべきで、常用するバージョンはインストーラーなどでインストールした`/usr/local/go`のほうを使うようにしましょう。と。
