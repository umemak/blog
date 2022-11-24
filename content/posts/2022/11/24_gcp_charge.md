---
title: "GCPの課金"
date: "2022-11-24"
tags: ["gcp"]

---

Cloud FunctionsでAPIデプロイしてから、課金が発生しているのに気が付いた。

200万回までは無料では？と思い詳細を見てみると、Cloud Storageの料金だった。

[料金  |  Cloud Functions  |  Google Cloud](https://cloud.google.com/functions/pricing?hl=ja)

> 関数が Container Registry に保存される場合、Container Registry には無料枠がないため、デプロイ後にわずかな料金が発生します。

これか。。

おそらく、設定ファイル変えて何度もデプロイしているのが悪いのだけど、ある程度設定が固まればそこまで増えることもないでしょう。きっと。
