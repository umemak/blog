---
title: "chiでproxy"
date: "2022-09-15"
tags: ["go", "chi"]

---

[grpc-gatewayでgRPCとREST両対応のサーバを作る | フューチャー技術ブログ](https://future-architect.github.io/articles/20220624a/)のサンプルで[mux.Handle("/docs/", docsProxy)](https://github.com/sayshu-7s/grpc-gateway-example/blob/9c97ffcb33ebfbe89610c32aa4ed0147eef9f4c9/cmd/gateway/main.go#L36)となっているところを、[go-chi/chi: lightweight, idiomatic and composable router for building Go HTTP services](https://github.com/go-chi/chi)を使っているので`router.Handle("/docs/", docsProxy)`と書いたところ、docsは見れるのに、cssやjsが404で見れなくて何でだろうと思った。

READMEにも
```go
	// Handle and HandleFunc adds routes for `pattern` that matches
	// all HTTP methods.
	Handle(pattern string, h http.Handler)
```
と書いてあって、`router.Handle("/docs/*", docsProxy)`としたら期待する動作をするようになった。

ドキュメント読むの大事。
