---
title: "CloudFunctionsのログ"
date: "2022-11-28"
tags: ["gcp","go"]

---

何もしないと、リクエストパラメータすらログに出力されないので、何かと不便。

[ログの作成、表示、処理  |  Google Cloud Functions に関するドキュメント](https://cloud.google.com/functions/docs/monitoring/logging?hl=ja#functions-log-structured-go)によると、標準出力や標準エラーに書き込めば良いが、Entry構造体を定義して、Stringメソッドを作り、logにPrintlnで渡せばもっと良い感じにできるらしい。

とりあえず、fmt.PrintlnでJSONを出力するようにしてみる。

が、デプロイでエラー。
```
ERROR: (gcloud.functions.deploy) OperationError: code=3, message=Build failed: go: golang.org/x/net@v0.0.0-20221014081412-f15817d10f9b requires
        golang.org/x/sys@v0.0.0-20220728004956-3c1f35247d10: missing go.sum entry; to add it:
        go mod download golang.org/x/sys; Error ID: 03a1e2f7
```

別の修正が影響しているようだ。。
