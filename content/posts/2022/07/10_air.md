---
title: "Airを試す"
date: "2022-07-10"
tags: ["go", "air"]

---

HTMLとかコード修正したときに手動で再起動するのが面倒なので、ホットリロードツールを導入してみた。

- [cosmtrek/air: ☁️ Live reload for Go apps](https://github.com/cosmtrek/air)

```sh
$ go install github.com/cosmtrek/air@latest
$ air init
$ air

  __    _   ___  
 / /\  | | | |_) 
/_/--\ |_| |_| \_ , built with Go 

mkdir /home/umemak/workspace/eventsite_go/tmp
watching .
watching cmd
watching cmd/eventsite
watching db
watching db/sql
watching model
watching model/user
!exclude tmp
watching web
watching web/template
building...
no Go files in /home/umemak/workspace/eventsite_go
failed to build, error: exit status 1
^Ccleaning...
see you again~
```
デフォルトだと、cmdの下のmain.goを見つけてくれない？

`air init`で作成された`.air.toml`を編集して、`cmd = "go build -o ./tmp/main ."`を`cmd = "go build -o ./tmp/main ./cmd/eventsite/"`にしたら動いた。

これで開発効率上がるはず。
