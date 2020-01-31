---
title: "NTT Tech Conference #4"
date: "2020-01-31"
tags: ["event", "ntt"]
thumbnail: https://connpass-tokyo.s3.amazonaws.com/thumbs/1d/d3/1dd3a210bb17f3ad13776f5286a8a16a.png
---

https://ntt-techconf.connpass.com/event/161866/

NTTグループのエンジニア有志が主催するカンファレンスイベントの4回目とのこと。
初参加です。

## Opening Keynote
* 参加者の半数がNTTグループ
  - NTTグループは919社もある
  - 30万人いるのでグループと言ってもでかすぎる
* エンジニアの有志が主催しています
* 前回から1年半
  - 退職エントリとか押しかけラグビーとか色々炎上していたので自粛していた

## Kubernetes基礎
### 吉村 翔太
* https://speakerdeck.com/yosshi_/kubernetesfalseji-chu
* 基本的なリソースを理解する
* 全体像
  - masterのAPIサーバーを経由して動いている
    - 状態はetcd
  - master
  - node
    - Container runtime
    - Kubeket
    - Kube-proxy
  - etcd
  - kubectl
* MasterとControl Plane cmponentsのち外
  - Master + Kubelet + Kube-proxy = Control Plane
  - ドキュメントによって表現に揺れがある
* etcsに行かない例外もある
  - 4パターン
  - /proxy, /exec, /attach, /logs
* マネージドで使うなら、kubectlとコンテナだけ使えれば良いことが多い
  - オンプレでやるなら全部理解しないと辛い
* Workload
  - Pod
    - コンテナのデプロイの最小単位
    - 複数コンテナをまとめたもの
    - メインのコンテナ＋サイドカーみたいな構成
  - ReplicaSet
    - Podの数を維持するためのリソース
    - Podのラベルで認識する
      - ラベルの付け方に注意する
    - selectorとtemplateのラベルは基本的に同じ。歴史的経緯で冗長になっている。
  - Deployment(deploy)
    - ReplicaSetを管理するリソース
    - RollingUpdateに使う
* Configuration
  - Configmap
    - 設定情報を保存するリソース
  - Secret
    - opaque
      - 使い方はConfigmapと同じ
      - エンコードされている
      - configmapと権限を分けて管理するのが良い
* Discovery & LB
  - ClusterIP
    - クラスタ内のアクセスを保証する
    - これもラベルで宛先を認識する
  - NodePort
    - クラスタ外からポート指定でアクセスする
    - ノード内に同じラベルのPodが複数あったら、どこに行くかはランダム
* Metadata
  - Namespace
    - 1つのクラスタを仮想クラスタにわかる
    - 障害の影響範囲でどう分けるか考える
      - 開発環境ならNamespace、本番環境はクラスタとか
      - クラスタ分けると管理コストが上がる







