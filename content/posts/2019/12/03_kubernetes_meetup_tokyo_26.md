---
title: "Kubernetes Meetup Tokyo #26"
date: "2019-12-03"
tags: ["event", "k8s", "kubernetes"]
thumbnail: https://connpass-tokyo.s3.amazonaws.com/thumbs/0b/e2/0be2c1c5921491c2c5db9ca69aff482c.png
---

今回は 2019/11/18-21 で開催された KubeCon + CloudNativeCon North America 2019 の Recap 会だそうです。
どちらも参加していないのでどんな話が聞けるのか楽しみです。

https://k8sjp.connpass.com/event/155240/

{{< x user="umemak8" id="1201797492385275905" >}}

## 18:15-19:15	受付開始


## 19:00-19:05	Opening (5min)


## 19:05-19:20	KubeCon + CloudNativeCon North America 2019 Overview
### Ian Lewis (@IanMLewis), Google
* ２つのイベントが同時開催だった
* 次回登壇したいヒトは明日までCFP受付中
* 12000人くらい。去年は8000人くらいだった。
* 女性11%はDev系カンファレンスでは多い方
* 関連イベントたくさん（スライドに入り切らない）
* CNCF End User Community
  - 日本の企業もいくつかある（もっとある？
* Kubernetes Project Update
  - 1.16
  - Ephemeral Containers
  - 毎月3000人以上がコントリビュートしている

## 19:20-19:40	Your Path to Production Ready Kubernetes hosted by Weaveworks
### 土田 智大 (dullest), 楽天株式会社
* Co-located eventのひとつ
* Production Readyのために
  - Liveness/Readiness Probe
  - Configmap
  - FGraceful shutdown
  - Twelve-Factor App
* ハンズオン資料
  - https://tinyurl.com/kubecon-2019-workshop
  - https://www.weave.works/product/cloud/
* curlでスクリプト叩くだけでデプロイできる
* Gitのファイルをもとにする（GitOps）
* Production Ready Checklist

## 19:40-20:00	Keynote: Seamless Customer Experience at Walmart Stores Powered by Kubernetes@Edge
### Junichi Yoshise (@jyoshise), Hewlett Packard Enterprise
* Walmartの決済の話
* POSシステムをクラウド化した（４年前）
* 通信コスト削減のためにエッジに処理を一部移動させる
* クラウドネイティブ化の動機
  - Dynamic deployment
  - Scalability
  - Resiliency
  - Observability
* エッジコンピューティングの動機
  - Low latency
  - Massive data
  - Privacy security
  - Local autonomy
  - Devices
* MEC(Mobile Edge Computing)
* データの同期
  - Edgeとクラウドで整合性が取れていないといけない
    - 商品の金額とか
* 物理的な制約
  - 各店舗にラックマウントサーバーを設置している
  - 基本的にEdge環境では、過酷な環境でメンテナンスフリーに近い形で稼働し続けなければならない
* K8sクラスタの更新
  - 遠隔地のクラスタ自体のデプロイを集中管理する仕組みが必要
* MECでは、端末は移動する前提
* スマートじゃないデバイスへの対応
  - KubeEdge
    - Device Twin
* アプリケーションのデプロイ
  - GitOpsが最適
  - WalmartはCDエンジンを自作
    - 今ならArgo flexやTectonが使える？
* Security
  - Secret管理
    - Vaultから撮ってきたsecretをetcdに一時的に保存するoperationを自作
    - クラウド側のみだとネットワーク切れたら使えなくなってしまうので

## 20:00-20:20	Running Apache Samza on Kubernetes - Weiqing Yang, LinkedIn Corporation
### 吉村翔太 (@yosshi_), NTT Communications
* samza
  - もともとはLinkedinが作ったストリーミング処理OSS
  - 似たものにSparkやFlinkがある
* 最近のHadoopの動向
  - オンプレで使う場合はディストリビューションを使う。主なものは３つ
  - ClouderaとHortonworksが統合。2021年くらい？
  - ClouderaDataPlatform
    - AWSをサポート。AzureとGCPも近々
* KafkaがHDFSなら、SamzaはMapReduceに当たる存在
  - KafkaもLinkedinが開発したOSS
  - Message queue, Message hub

## 20:25-20:55	懇親タイム sponsored by Yahoo! JAPAN


## 20:55-21:15	How Yelp Moved Security From the App to the Mesh with Envoy and OPA
### 鳥居隆史 (@ttorii0609), Dell EMC
* Security
  - K8s is NOT secure by default
    - 基本フルオープンなので、ザル。
    - 9個のプラクティス全部やれ
  - K8sのセキュリティは今アツい
* Open Policy Agent(OPA)
* mTLS
* OPAを使うにあたっての課題
  - OPA Policy Managerを作った
* セキュリティを考えるとサービスメッシュは必要
* Scope Creep
  - 要件がどんどん広がっていく様

## 21:15-21:35	The Release Team Shadow Program - Mentoring For the Future - Guinevere Saenger, GitHub & Lachlan Evenson, Microsoft
### Yang Li (@idealhack), Kubernetes community
* 


