---
title: "CloudFunctionsのログ"
date: "2022-11-28"
tags: ["gcp","go"]

---

何もしないと、リクエストパラメータすらログに出力されないので、何かと不便。

[ログの作成、表示、処理  |  Google Cloud Functions に関するドキュメント](https://cloud.google.com/functions/docs/monitoring/logging?hl=ja#functions-log-structured-go)によると、Entry構造体を定義して、Stringメソッドを作り、logにPrintlnで渡せば良いらしい。
