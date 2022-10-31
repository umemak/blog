---
title: "SAMでIP制限"
date: "2022-10-31"
tags: ["aws", "sam"]

---

SAMを使ってデプロイしたLambdaの、リクエスト元のIPアドレスを制限したいとき。

Lambdaに制限を入れるのではなく、API Gatewayの設定でいける。

[api gateway + samでapiの環境を作る(ip制限) - Qiita](https://qiita.com/cony0413/items/18551d314b445a864e87)

ここにたどり着くまでに、Lambdaをセキュリティグループに入れてみたりしたけど効かなかったりで割と苦労した。
