---
title: "Cloud Functionsのデプロイでエラー"
date: "2023-10-08"
tags: ["GCP"]

---

久しぶりにデプロイ実行したら、エラーで中断してしまった。

エラーメッセージを見ると、いっこ前のイメージが見つからないみたいなやつで（コピペ紛失）、そういえばコスト削減しようとして、Storageのライフサイクルを1日とか最短にしたのを思い出した。

[Cloud Functions のトラブルシューティング  |  Google Cloud Functions に関するドキュメント](https://cloud.google.com/functions/docs/troubleshooting?hl=ja#missing-gcr)はちょっと違うけど、関数を削除してやり直せば良さそうなので、そうした。

無事解決。
