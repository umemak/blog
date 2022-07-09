---
title: "Revel入門"
date: "2022-07-09"
tags: ["go", "revel"]

---

ちょっとしたWebアプリを作りたくなったので、GoでRailsみたいなフレームワークないのかなと探した。

- [revel/revel: A high productivity, full-stack web framework for the Go language.](https://github.com/revel/revel)

が近そうだったので、試してみた。

```sh
$ go install github.com/revel/cmd/revel@latest
go: downloading github.com/revel/cmd v1.1.2
go: downloading github.com/agtorre/gocolorize v1.0.0
go: downloading github.com/jessevdk/go-flags v1.4.0
go: downloading github.com/revel/config v1.1.0
go: downloading github.com/revel/log15 v2.11.20+incompatible
go: downloading github.com/mattn/go-colorable v0.1.8
go: downloading gopkg.in/natefinch/lumberjack.v2 v2.0.0
go: downloading gopkg.in/stack.v0 v0.0.0-20141108040640-9b43fcefddd0
go: downloading github.com/pkg/errors v0.9.1
go: downloading github.com/fsnotify/fsnotify v1.4.9
go: downloading github.com/mattn/go-isatty v0.0.14
go: downloading github.com/inconshreveable/log15 v0.0.0-20201112154412-8562bdadbbac
$ revel new -a events_go -r
revel: command not found
```
おや？パスが通ってない？
```sh
$ ~/go/bin/revel new -a events_go -r
Revel executing: create a skeleton Revel application
Your application has been created in:
   /home/umemak/workspace/events_go
ERROR 12:08:17   file.go:387: Error                                    errors="[-: no required module provides package github.com/revel/revel; to add it:\n\tgo get github.com/revel/revel]"  seeking=github.com/revel/revel count=1 App Import Path=github.com/revel/revel filesystem path=github.com/revel/revel
Downloading related packages ... completed.
WARN  12:08:20 harness.go:179: No http.addr specified in the app.conf listening on localhost interface only. This will not allow external access to your application 
Change detected, recompiling
Parsing packages, (may require download if not cached)... Completed
WARN  12:08:23  build.go:242: Detected missing packages, importing them packages=3 
Downloading related packages ... completed.
INFO  12:08:26    app     run.go:34: Running revel server                      
INFO  12:08:26    app   plugin.go:9: Go to /@tests to run the tests.           
Revel engine is listening on.. localhost:40439
Revel proxy is listening, point your browser to : 9000

Time to recompile 5.818458007s
Change detected, recompiling
Revel engine is NOT listening on.. localhost:40439

Revel exited normally

Parsing packages, (may require download if not cached)... Completed
INFO  12:09:52    app     run.go:34: Running revel server                      
INFO  12:09:52    app   plugin.go:9: Go to /@tests to run the tests.           
Revel engine is listening on.. localhost:40439
Revel proxy is listening, point your browser to : 9000

Time to recompile 1.765697354s
2022/07/09 12:09:52 http: proxy error: dial tcp 127.0.0.1:40439: connect: connection refused
```
なんかエラー出てますね。。
楽をしようと思ってフレームワーク導入するのに、初手で躓くのはちょっと困る。

別の手段探そう。
