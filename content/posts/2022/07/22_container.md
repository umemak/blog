---
title: "コンテナ実行環境比較"
date: "2022-07-22"
tags: ["aws", "azure", "gcp"]

---

AWSとAzureとGCPで、コンテナ実行環境の比較をしてみたくなった。

GCPの[Cloud Run: コンテナを秒単位で本番環境にデプロイ  |  Google Cloud](https://cloud.google.com/run?hl=ja)みたいなやつ。

AWSは[AWS App Runner – フルマネージド型のコンテナアプリケーション - Amazon Web Services](https://aws.amazon.com/jp/apprunner/)、Azureは[Azure Container Apps | Microsoft Azure](https://azure.microsoft.com/ja-jp/services/container-apps/#overview)が比較対象となるかな？

AWSは選択できる最低スペックが1vCPU/2GBメモリなので、GCPとAzureもこれに合わせた見積もりにする。
なお、メモリはAzureは最低1GBから、GCPは最低128MBから選択できる。

Cloud Run
```
Region: Tokyo
CPU Allocation Type: CPU is only allocated during request processing
CPU: 1
Memory: 2 GiB
CPU Allocation Time: 2,500,000 vCPU-second
Memory Allocation Time: 5,000,000 GiB-second
Requests: 100,000,000 requests
USD 106.48
```

Azure
```
Monthly: $108.80
```

AWSの料金計算ツールにApp Runnerが入っていない・・？
よくわからないけど81.48USDくらいかな。。

月間リクエスト数を100,000,000に設定したのが上記値段で、一桁減らすとGCPもAzureも5.3USDくらいに落ちる。

メモリやCPU変えてもそこまで劇的に変化しないので、リクエスト数がコスト計算のカギになりそう。

いや、vCPU-sとGiB-sで比較するのが正解か。

| |GCP|Azure|AWS|
|---|---|---|---|
|vCPU-s|0.0000240|0.0000240|0.0000225|
|GiB-s |0.0000025|0.0000030|0.0000025|

AWSが若干安いけれど、「プロビジョニングされたコンテナインスタンス」の分が0.00000194加算されるとほぼ誤差。

つまり金額は選定の決め手にならない。

使い勝手なんかは、実際触ってみないとなんとも。。
