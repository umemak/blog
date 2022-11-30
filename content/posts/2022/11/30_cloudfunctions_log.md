---
title: "CloudFunctionsのログ"
date: "2022-11-30"
tags: ["gcp","go"]

---

デプロイのエラーは、`go clean -modcache`して`go.sum`削除して`go.mod`のrequire全削除して`go mod tidy`したら直った。
何が効いたのかはわからない。

ログは、JSON形式で出力しないといけないのかと思ってそのように書いてみたら、そのまま記録されて構造化されなかった。

集計するものでもなければ、とりあえずfmt.Printfで書いておけばそのまま確認できるのでOK。
