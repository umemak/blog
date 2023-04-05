---
title: "KQL入門"
date: "2023-04-05"
tags: []

---

Azure Container Appsのログ、ログストリームで何とかやってきたのだけれど、そろそろ検索もできるようになっておかないと駄目な感じになってきたので、KQLのチュートリアルを眺めてみた。

ところで、どの記事も当たり前に使っている`Kusto`って何？
ググってもよくわからなかったので、ChatGPTに聞いてみた。

> Kustoは、Microsoft Researchによって開発され、2015年にAzure Data Explorerとして公開されました。

もともとは製品名というかプロジェクトコードみたいなものだったのかな。

- [Kusto 照会言語 (KQL) の概要 - Azure Data Explorer | Microsoft Learn](https://learn.microsoft.com/ja-jp/azure/data-explorer/kusto/query/)
- [チュートリアル: 一般的なKusto 照会言語演算子について学習する - Azure Data Explorer | Microsoft Learn](https://learn.microsoft.com/ja-jp/azure/data-explorer/kusto/query/tutorials/learn-common-operators?pivots=azuremonitor)
- [Log Analytics のチュートリアル - Azure Monitor | Microsoft Learn](https://learn.microsoft.com/ja-jp/azure/azure-monitor/logs/log-analytics-tutorial)

とりあえずこの辺りを一通り読み込めば何とかなりそうな気がした。
