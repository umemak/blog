---
title: "Docker swarm modeを知る"
date: "2020-11-07"
tags: ["docker"]
---

複数の仮想サーバーでdocker-composeで起動したコンテナの管理をする方法を調べていて、swarm modeにたどり着いたので調べたことを残す。

* コマンドでモード切替
  - 有効化：`docker swarm init`
  - 無効化：`docker swarm leave --force`

* シングルノードでも試せる
  - シングルノードの場合は、init時の`--advertise-addr`指定は不要

* Docker swarmとswarm modeは別
  - Docker 1.12からDocker本体にswarmが取り込まれて、swarm modeになった
  - 1.12以降でもswarmは使えるが、swarm modeの方が簡単に利用できる

* 複数ノードで構成する場合は、コンテナイメージをレジストリに格納する必要がある

* 複数ノードで構成する場合は、ノード間でいくつかのポートの通信を許可しておく必要がある
  - TCP port 2377 は、クラスタ管理通信のため
  - TCP と UDP の port 7946 は、ノード間の通信のため
  - UDP port 4789 はオーバレイ・ネットワーク・トラフィックのため

* swarmにサービスをデプロイすると、タスクが作成される
  - AWSのECSに似た概念？

* サービスのデプロイは、`docker-compose up` コマンドではなく、`docker service create`を使う
  - シングルノードの場合は、WARNINGは出るがdocker-composeも使える

* swarmクラスタの可視化ができる`portainer`というOSSがある

## 参考リンク
* [Docker swarm mode でDockerのオーケストレーションツール入門 - Qiita](https://qiita.com/KuwaK/items/a72706e0de49adda2c7f)
* [Single node docker swarm でお手軽 rolling update | 1Q77](https://blog.1q77.com/2018/10/rolling-update-on-single-node-docker-swarm/)
* [portainer/portainer: Making Docker and Kubernetes management easy.](https://github.com/portainer/portainer)
* [swarm モードの概要 | Microsoft Docs](https://docs.microsoft.com/ja-jp/virtualization/windowscontainers/manage-containers/swarm-mode)
* [Swarm モードの重要な概念 — Docker-docs-ja 19.03 ドキュメント](https://docs.docker.jp/engine/swarm/key-concepts.html)
* [Docker Swarmで学ぶサービスメッシュ - Qiita](https://qiita.com/Brutus/items/b3dfe5957294caa82669)
* [Swarm で Compose を使う — Docker-docs-ja 17.06 ドキュメント](https://docs.docker.jp/compose/swarm.html)
* [Docker Swarm mode 入門と ECS との比較 - Google スライド](https://docs.google.com/presentation/d/1boiXkW8cgyaIRBm6wV3zVEzH3v-Sfszh6qZFnFnwSMs/htmlpresent)
