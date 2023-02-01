---
title: "goでmissing go.sum entry cacheエラー"
date: "2023-01-16"
tags: ["go"]

---

`go build`しようとすると`missing go.sum entry cache`なエラーが出る。

ググっても`go mod tidy`すれば直る的なものしかヒットせず。

`go clean --modcache`してみてもダメ。

`go run`だと実行できてしまうので余計訳が分からない。
