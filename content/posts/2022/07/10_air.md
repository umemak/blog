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

ビルドファイルとビルドログがtmpに出力されるので、`.gitignore`に`tmp/`を追加した。

[DockerコンテナでgolangをホットリロードするAirを導入](https://zenn.dev/ajapa/articles/bc399c7e4c0def)を参考に、Dockerでもいけるようにしてみた。

Dockerfileはgo getではなくgo installでも大丈夫だった。
gitのインストール不要。
```Dockerfile
FROM golang:1-alpine

RUN go install github.com/cosmtrek/air@latest

WORKDIR /app

CMD ["air"]
```
