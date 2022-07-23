---
title: "データベース比較"
date: "2022-07-23"
tags: ["aws", "azure", "gcp"]

---

昨日はコンテナ実行環境の比較、今日はマネージドDB（MySQL）を比較してみる。

- [Amazon RDS for MySQL （MySQLのためのマネージドリレーショナルデータベース） | AWS](https://aws.amazon.com/jp/rds/mysql/?nc=sn&loc=0)
- [Cloud SQL for MySQL マネージドデータベース  |  Cloud SQL: リレーショナル データベース サービス  |  Google Cloud](https://cloud.google.com/sql/mysql?hl=ja)
- [Azure Database for MySQL - マネージド MySQL データベース | Microsoft Azure](https://azure.microsoft.com/ja-jp/services/mysql/)

リージョンは東京で、シングル構成の前払いなし。

|  | GCP | Azure | AWS |
|---|--:|--:|--:|
|1vCPU/2GiB/30GB|57.57USD|41.56USD|42.10USD|

GCPが高い。

vCPUとメモリはAzureの選択肢に合わせた。
AWSだともっと低いスペックも選択できるので、開発やデモで使うならAWSか。
