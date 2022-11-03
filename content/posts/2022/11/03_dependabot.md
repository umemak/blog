---
title: "GitHubのセキュリティアラートを片付ける"
date: "2022-11-03"
tags: ["GitHub", "npm"]

---

試しにexpoとかnextとか使ってみるのに作ったリポジトリでパッケージのセキュリティアラートが割とよく来るけど、放置気味だった。

きれいにしたいと思い立って、やってみた。

まず、`npm update`だとあまり解消しない。
コンフリクトとか言われて、個別パッケージ指定してもやっぱりダメな感じ。正直よくわからない。

[package.json に記載されているパッケージのバージョンアップ方法 【 npm-check-updates, outdated 】 - Qiita](https://qiita.com/sugurutakahashi12345/items/df736ddaf65c244e1b4f)を参考に、`npx -p npm-check-updates  -c "ncu"`して`npx -p npm-check-updates  -c "ncu -u"`してpushしたら、きれいに解消した。
