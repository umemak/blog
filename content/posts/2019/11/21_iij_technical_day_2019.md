---
title: "IIJ Technical DAY 2019"
date: "2019-11-21"
tags: ["event", "iij"]
thumbnail: https://connpass-tokyo.s3.amazonaws.com/thumbs/d9/69/d969ecd978b7ee81e72e9379791a9e13.png
---

https://iij.connpass.com/event/151720/

https://eng-blog.iij.ad.jp/archives/4102

IIJmioでお世話になってます

2003年から毎年開催しているそうですが、初参加です。

インフラ周りはあまり直接触れることがないので、どこまで話についていけるか。

## 13:30 ~ 13:40	開会のご挨拶
### IIJ 取締役 CTO 島上 純一
* 技術を通じてIIJを知ってもらいたい

## 13:40 ~ 14:20	講演1「安全なデジタル通貨流通を支えるアーキテクチャとエンジニアリング」
### ディーカレット テクノロジーグループ マネージャ 河津 拓哉
* ブロックチェーンの話
* 価値の
  - 保管
  - 交換
  - 送受
* サービスアーキテクチャ
  - APIゲートウェイを挟んだマイクロサービス
  - 取引の部分が一番大きく、重要
  - 決済の部分はこのサービス独特なもの
* 認証まわり
  - OpenID Connect の実装
  - Two-way/TLS
  - Restrict(IP Based)
  - Traffic Policy
* 高信頼性（バックエンド）
  - サーバーの調達から自前で行う
  - 堅牢な設計、完全なコントロール
* 俊敏性（フロントエンド〜ゲートウェイ）
  - アジャイルな組織・手法で
  - 小さく・速く作ってフィードバックを回す
  - GCPを利用
* コンテナの話
  - ドメインの分割が一番難しい
  - latestタグやバージョン未指定でのパッケージアップデートはNG
  - rootユーザーでプロセスを起動させるのもNG
* k8s自前で管理するか
  - とても大変なのでマネージドサービスを使う
  - そうするとIaCが捗る

## 14:20 ~ 14:30	休憩


## 14:30 ~ 15:10	講演2「IIJのサーバインフラはここまでやっています」
### IIJ 基盤エンジニアリング本部 システム技術部 基盤運営1課長 高畑 雅弘
* サービス基盤インフラNHN
* データセンターが抱える課題
  - コスト
    - 土地代が高い、狭い
  - ラックあたりの電力許容量が少ない
    - 建物自体の配電設計や空調も限界
    - 他のテナントと電気の取り合い
  - ラックの収容台数を最大化できない
    - ネットワークスイッチのポート数
  - 供給電力と空調能力のバランス
    - 詰めすぎると空調が追いつかない
      - サーバーファインが回って電力消費が増える
    - 空調に合わせると台数を増やせない
* コスト低減策
  - 設備投資
  - 運用コスト
* 土地・電気の問題を解決したデータセンターを作る
  - 土地・建物、電気、空調
* 事業者向けに最適化されたデータセンターを作る
  - データセンター開発部門とサーバインフラ開発部門が共同で検討
  - ラックの高さを増やせないか？
    - 日本国内では製造されていないが、海外ではある
  - サーバーをより多く搭載できないか？
  - 一度にたくさんのサーバーを納品できないか？
  - 奥行きの長いサーバーを搭載できないか？
    - 最近800mm超えるものがある
    - 配線など考えると1000mmでは足りない
  - ラック前のスペースが狭い
    - ラック設置後の取り出し作業などができなくなる
  - フリーアクセスフロア
    - 年月が進むとケーブルの地層ができてしまう
* 新しいサーバーインフラを作ろう
  - Open Compute Project(OCP)
    - ハードウェアのオープンソース化を推進している団体
    - 利点
      - 本当に必要なパーツのみで構成することができるので、調達コスト減、電力コスト減
      - 個別に機能を実装してもらえる可能性がある
      - 交換可能なパーツ交換に工具が不要
    - 欠点
      - 為替の影響を受ける
      - 専用ラックと電源が必要
      - テストは利用者側が実施する
      - 保守は自前でパーツ交換のみ
      - メーカーとのやり取りは英語や中国語
    - 調達コスト・消費電力ともに減

## 15:15 ~ 15:35	コーヒーブレイク
* 神楽坂「亀井堂」のパン

## 15:35 ~ 16:10	講演3「Untangling the world-wide mesh of undersea cables：世界に張り巡らされた海底ケーブルネットワークをひもとく」
### IIJイノベーションインスティテュート（IIJ-II） 主任研究員 Zachary Bischof （ビショフ ザカリー）
* 海底ケーブルを使った通信は99%
* 障害が起きて孤立化することも
* なぜ今海底ケーブルの研究をしているか
  - ケーブルのEOL
  - 自然災害
* ケーブルが長くなれば事故のリスクも増える
* tracertではどの海底ケーブルを通っているかまではわからない
  - わかるようにしたい
    - ルーターの物理的な位置を特定する
    - RTTをもとに海底ケーブルを使っている可能性がある場所を推測する
    - 地上の距離を測る（Google map）
    - 過去のケーブルアクティビティデータをもとに推測する
  - こうすることで、どのケーブルが重要なのかが見えてくる
    - SEA-ME-WE3
      - https://www.submarinecablemap.com/#/submarine-cable/seamewe-3

## 16:10 ~ 16:20	休憩


## 16:20 ~ 17:00	講演4「セキュリティ動向2019」
### IIJ セキュリティ本部長 齋藤 衛
* 標的型攻撃
  - 2003〜2008年頃は政府機関が対象、2011年以降に中小企業も狙われてきている
  - 暗号資産関連組織が狙われる
* ランサムウェア
  - 最近は検出数が減少傾向
  - ターゲットが絞り込まれている
    - 公共サービスや医療機関など身代金を払いそう（払わざるを得ない）なところ
* DDoS攻撃
  - SYN/ACK攻撃
    - 正常な通信との判別が難しい
  - 恐喝DDoS攻撃
    - 20〜30Gbps程度の攻撃でもネットワークによっては影響ある
* フェイクニュース
  - 正月のカニ
  - 本物の情報でも、順番を並べたりすることで受け取りての印象操作をすることができる
    - Facebookが実験した
  - マイクロターゲティング広告
    - ネット上の行動履歴など個人情報を詳細に分析できるようになってきている
  - ブレグジット問題
  - なにかの判断は原典にあたってから実施しよう

ここまでで家の用事のため撤収。データセンターの話面白かった。
