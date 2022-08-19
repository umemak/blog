---
title: "AWS App Runner"
date: "2022-08-19"
tags: ["aws"]

---

[AWS App Runner – フルマネージド型のコンテナアプリケーション - Amazon Web Services](https://aws.amazon.com/jp/apprunner/)

ちょっと使ってみた。

[App Runner の新機能 — Amazon Virtual Private Cloud (VPC) をサポート | Amazon Web Services ブログ](https://aws.amazon.com/jp/blogs/news/new-for-app-runner-vpc-support/)を見て、RDSに接続してみようと。

コードリポジトリはGitHubしか対応していないし、GitHub側にインストールしないといけないものもあるようなので、とりあえずECRを使ったパターンで。

IAMデータベース認証を使用するためのロールがよくわからず（ポリシーとロール作ったら選択できるようになると思ったんだけど、出てこない（たぶんロールの作り方が間違っている））、通常のDB認証にした。

あとはVPCとかSGはRDSと同じ物を指定して問題なさそう。

で、デプロイに5分くらいかかって、意外と長い印象。
設定変更とかの反映も数分かかってる感じ。

負荷かけたときのスケールアップがどれくらいかかるのかは、試していない。

サーバーを気にしなくて良いのは便利だと思う。
