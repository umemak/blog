---
title: "Bonfire Backend #4"
date: "2019-11-26"
tags: ["event", "yahoo"]
sumbnail: "https://connpass-tokyo.s3.amazonaws.com/thumbs/60/1b/601b3df098ca1a61f2e0f9a8caa1ac74.png"
---

https://yj-meetup.connpass.com/event/153658/

初参加です。


## 19:00	開場・受付開始	

## 19:30	イントロ・乾杯	


## 19:35	ヤフーのナビゲーション系のバックエンドサービスの課題をk8sで解決した話
### 高木 克彰(@tkgtransit) ◆ ヤフー株式会社
* ナビゲーション
  - マップの徒歩ナビ
  - 乗り換えナビ
* 従来のアーキテクチャ
  - エンジンデータはそれぞれ１台の仮想サーバーが担当
  - C++, Apacke Module
  - 課題
    - IFが異なるだけで基本ロジックはほぼ同じ
    - データ更新に半日
    - 脆弱性対応が多い、手作業
* 改善後
  - API層を統合
    - 社内PaaSに移行
  - エンジン層
    - 社内CaaSに移行
    - バイナリデータはinit comtainerで取得してオンメモリに展開
  - データの更新はk8sのcronで実行
* パイプラインはscrewdriver使っている

## 19:50	プライベートクラウドをk8sで刷新して良かった話
### 鶴田貴大 ◆ サイボウズ株式会社
* 自社製プライベートクラウド
  - OpenStackは使っていない
  - Ubuntu
    - 14.04から16.04へのアップグレードに２年くらいかかった
  - コンテナもほぼ使っていない
* インフラ刷新
  - necoプロジェクト
  - CKE(Cybozu Kubernetes Engine)
  - Certifiedになった
* 目的
  - 運用コスト低減
  - スケーラビリティ向上
* K8sを選んだ理由
  - 圧倒的に流行っていたから
* CoreOS採用
  - コンテナ用軽量OS
* GitOps
  - Argo CDを使用
* テナント
  - チームごとに権限を分離
  - ほかテナントに影響しないように
  - 単一のk8sクラスターですべてのテナントを賄っている
* 開発環境
  - クラスタを共同利用
    - うっかり壊すと大変
  - Kindに変更
    - ローカルPCでも動かせる
* Teleport
  - 多機能踏み台サーバー
  - ターミナルの入出力を録画できるので、監査に使える

## 20:10	PFNにおける二種類のKubernetesクラスタ
### 太田佳敬(@ota42y) ◆ Preferred Networks
* https://speakerdeck.com/ota42y/pfnniaru2tufalsekubernetes
* 自社GPUクラスタ
  - 機械学習のためにマシンリソースが必要
  - 2500以上
  - これの制御をk8sで行っている
* WebApplication用
  - aws EKSに構築
  - EKSを使うほどではないが、K8sを使い慣れているのでECSではなくEKS
* K8sのNetwork Isolation
  - 1つのクラスタに関係ないアプリが複数同居している
  - 相互通信しないようにネットワーク分離が重要
  - Network Policies
    - PodやNamespace単位で通信を制御できる標準機能
    - アプリケーションごとにNamespaceを分けて相互アクセスを禁止した
    - デフォルトでは通信許可設定なので設定忘れを抑制したい
      - Calicoを利用してデフォルトで通信禁止に設定
        - https://github.com/projectcalico/calico
        - Namespace内部の通信も禁止になるので、そこは許可する
        - kube-systemも許可する。禁止したままだとkube-dnsも使えなくなってしまう
        - orderで優先順位を決める
    - Network PolicyでALBを指定（許可）できない
      - Subnet構成で回避

## 20:30	小休憩	


## 20:35	K8Sで画像PFを1年半運用してみた振り返り
### 山田 拓也 ◆ ヤフー株式会社


## 20:50	k8s初心者がgRPC × envoyを導入したら色々苦労した話
### 信原 有志 ◆ ヤフー株式会社


## 21:00	懇親会

## 22:00	終了	
