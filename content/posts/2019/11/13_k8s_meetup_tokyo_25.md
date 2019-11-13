---
title: "Kubernetes Meetup Tokyo #25"
date: "2019-11-13"
tags: ["kubernetes", "event"]
---

https://k8sjp.connpass.com/event/150873/

何度か応募するも抽選に落ちて、初参加です。

ストレージ系の話が中心です。

## 18:30~19:00	受付開始 (19:30まで)、ソーシャル	


## 19:00~19:05	Opening (5min)	


## 19:05~19:35	入門、Kubernetes Persistent Volume (30min)
### 坂下 幸徳（Twitter: @ysakashita3, GitHub: ysakashita), ゼットラボ株式会社
* ストレージの苦手意識を払拭する
* データプレーンとコントロールプレーン
  - データ：格納と転送担当
  - コントロール：管理担当
* ストレージの種別
  - ブロック：内蔵ドライブと同じRawデバイス：性能High：DBやOS
  - ファイル：ネットワークドライブ：性能Mid：ファイル共有
  - オブジェクト：オブジェクト単位でHostからはHTTPアクセス：性能Low：写真や動画格納
* Persistentとは
  - Ephemeralの対義語。
  - 永続的
* ストレージのモデル
  - PersistentVolumeClaim, PersistentVolume, StorageClass
  - オブジェクトストレージ以外（オブジェクトストレージはそもそもHTTPでアクセスできるので）
* リソースの範囲と権限
  - SC, PVはすべてのNamesoaceで共通
* pvc
  - Volumeの要求仕様を表すリソース
* ロックメカニズム
  - ブロック：LBAのため、ロックメカニズムを持っていない
    - 複数ホストから同時に書き込まないようにする
  - ファイル
    - ファイル単位でロック
    - 複数ホストから読み書き可能
* pv
  - Volume を表すリソース
* sc
  - ストレージプールを表すモデル
  - Provisionerがストレージ装置のAPIを呼び出す
* CSI(Container Storage Interface)
  - コンテナオーケストレーション向けの標準仕様
  - K8s 1.13 で GA
* StatefulSet(sts)
  - pv, pvcを便利かつ安全に使う
* Rolling Update（セルフヒーリングも同様）
  - podは再作成
  - pv, pscはそのまま
* FAQ
  - ストレージは何を選んだら良いか
    - 用途、データの価値による
  - CinderとA社どちらが良いか
    - 比較対象が異なる
    - K8sやCSIがサポートしてないならCinderを挟むのがあり
  - DB用途
    - 特別な理由がなければブロックストレージが良い
    - 性能問題、ロックメカニズムの問題
    - ファイルストレージはSyncで書き込まれる保証がない
  - Deploymentでpv使ってもよいか
    - ストレージに優しくないのでStatefulSetがオススメ
    - RWXをサポートしていないストレージはsts一択

## 19:35~20:10	KubernetesにおけるCSIについて (30min)
### 早川 大貴 (Twitter: bells17_, Github: bells17), 株式会社IDCフロンティア
* https://docs.google.com/presentation/d/1S0FcCAgZn11ZFbJfU2eUhOa--vONqrsd0waRvwoTBcE/edit
* CSI移行のモチベーション
  - ストレージプロバイダ
    - CSIプラグインを実装するだけで各種コンテナオーケストレーター(OC)に対応できる
  - K8s
    - ボリュームプラグインを本体から除外できる
    - バイナリサイズの削減など期待
* 機材トラブル
* CSIで定義されている仕様
  - ドライバの通信方法や提供方法
    - コンテナイメージ形式で提供する
  - 提供する機能
  - gRPCのインターフェース
* RPC service
  - Identity Service
  - Controller Service
  - Node Service
* K8sとCSIの連携
  - Controller Plugin/Node Pluginをサイドカー的に使用する

## 20:10~20:45	How to develop the high-available Redis database application on Kubernetes (en/英語) (30min)
### Ran Xu (Github: fengzixu Twitter: Haierdi0715)
* Higily Reliable Data
  - backup
* High Available Service
  - data link
    - LBで分散管理

## 20:45~21:10	懇親タイム sponsored by CyberAgent	


## 21:10-21:30	LT大会 (5min x 5)	-
### 
* https://speakerdeck.com/ytaka23/kubernetes-meetup-tokyo-25th
* Topology Spread Constraints
  - v1.16でα版
  - 設定次第でデッドロックになる可能性も

###
* https://www.slideshare.net/inajob/kubeweekly/inajob/kubeweekly
* K8s情報のキャッチアップ
  - https://kubeweekly.io

### 
* https://speakerdeck.com/int128/deploy-the-cluster-autoscaler-with-terraform-and-helmfile-monitor-with-prometheus
* Cluster Autoscalerのデプロイとモニタリング
  - Terraform, Prometheus

###
* Rook（るーく）/ Ceph
  - Host-based と PVC-based
  - Nodeに特別なNodeが必要なくなる

### 
* Kubespray
* CentOSで動かなくてCoreOSにしたら動いた
* マネージドサービスを使ったほうが楽

