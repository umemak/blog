---
title: "GitHub ActionsでAzure Storage Blobにファイルをアップロードする"
date: "2023-08-01"
tags: ["Azure", "GitHub"]

---

[GitHub ActionsからAzure上のIPアドレス制限済みリソースにアクセスする｜クラウドテクノロジーブログ｜ソフトバンク](https://www.softbank.jp/biz/blog/cloud-technology/articles/202210/gha-azure-ip/)を見ながらやってみた。

例だとSleepが10秒だけど、試した環境だとエラーになったので、15秒にしたら通った。

あと、`--account-name`指定ではアップロードできず、`--connection-string`で試したらできた。

Azureの権限周りがいまいち分かっていないので、つらい。
