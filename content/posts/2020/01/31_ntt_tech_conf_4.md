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

## 1870件以上のカーネルの不具合修正に貢献した再現用プログラムを自動生成する試験自動化技術
### 藤井 秀行
* https://www.slideshare.net/nttdata-tech/syzkaller-linux-kerneltestingnttdata
* GoogleのDmitry Vykovが開発したsyzkaller（シスコーラー）
  - Go言語
  - Googleとしては非公式
* ファジング
  - 未知の不具合や脆弱性の検出に適したテスト手法
  - Linuxのセキュリティ品質向上に貢献
  - リリース前にセキュリティ脆弱性が修正されるようになりCVEが現象してきている
* ドキュメント調査
  - 入力データの生成の仕組みが肝
  - ソースカバレッジも気にする
  - カーネルの入力インターフェースはシステムコール
  - syz_manager
    - 仮想化ホスト上に存在するプロセス
    - syz-fuzzerに指示を行う
  - workdir
    - 入出力ファイルを置く
  - syz_fuzzer
    - 試験環境内に存在するプロセス
    - syz_executorを生成
  - syz_eecutor
    - システムコールを送る
* 動作確認
  - 20分くらいで見つかった
* 試すなら私物PC、私物ネットワークでやる。絶対。

## Coffee Break
* Showcaseで「技術系業務自動化のエンジン展示」の説明を聞きました。
  - TSVを入力として、コマンドを実行する
  - sshとかtelnetとかブラウザとか操作できる
  - これを横連携させて実行できるのは（開発開始した当時は）あまりなかった
  - OSSとして公開したいが、まだ調整中。
  - 公開されたら試してみたいと思います。

## React HooksとGraphQLで社内レガシーサービス巻き取ってみたらものすごくはかどった話
### 奥井 寛樹
* https://speakerdeck.com/hrk091/react-hookstographqldeshe-nei-regasisabisuwojuan-kiqu-tutemitaramofalsesugokuhakadotutahua-153983bf-84bd-4be7-83c4-c8fa826db79e
* フロントエンド＋BFFの話
* うまく行った理由
  - フレームワークによる抽象化がうまく、ユースケースにフォーカスした開発ができた
  - GraphQLエコシステムが充実していた
* React Hooks
  - React FCでStateを扱えるようにするフレームワーク
  - React lifecycle eventを意識しなくて良くなる
  - Context APIの使い勝手が向上
* GraphQL
  - APIプロトコル
  - RESTより柔軟
  - クライアント側でレスポンスを定義できる
* Graphene
  - PythonのGraphQLフレームワーク
  - ORMモデル定義からAPIを自動生成してくれる
* Apollo
  - GraphQLのライブラリ
  - バックエンドとフロントエンドクライアントを提供
  - Reactに標準対応している
* 漸近的型付け
  - 動的型付け言語に後で型をつけること

## 海外講演を通じて得られた知見(英語力＋α編)
### 神原 健一
* https://speakerdeck.com/korodroid/ntt-tech-conference-hai-wai-jiang-yan-wotong-zitede-raretazhi-jian-ying-yu-li-abian
* https://qiita.com/korodroid/items/bf029f7aad896731771a
* 英語を学ぶ目的を具体的に描く
  - 海外カンファレンスで講演する
* skills
  - reading, listening, writing, speaking
  - 自分のレベルの把握
  - どのスキルをどのくらいにしたいのか
* 先人に学ぶ
  - SlideShare, Speaker Deck
* 登壇→フィードバック→次回への反映のループ
  - 習うより慣れろ
* 頭の中にある考えをリアルタイムに英語で話す
  - Cheat Strategy
    - スライドのノートにセリフを全部書く
    - →会場を見ないで読むだけになってしまった。失敗。
  - 自身を持って自分の言葉で話すことが大事
* tips for communications
  - 自分から話しかける
  - お互いの作品を見せ合う
* 英語の教材の選び方
  - （自分の目的とレベルに合わせて選ぶしか）ない
  - ノンネイティブ英語の練習
    - ノンネイティブスピーカーのセッション動画
  - ネイティブ英語の練習
    - TOEIC公式問題集
  - 英語の「音」の聞き分け
    - 英語耳
* オンライン英会話
  - 体験レッスンやってみると良い
* 英語を話す機会を増やす
  - 面倒なことこそ、修行のチャンス
  - 知識＜＜＜実践
  - ビジネスだけではなくプライベートでも

## パワポをよくしただけなのに〜デザインの力で会社に貢献するチームの紹介
### 鈴木 雅貴
* https://www.slideshare.net/suzukima/ss-226433621
* 2つのデザイン支援チームができてしまった
  - 統合した
* 製品の価値・魅力向上
* 社外のデザイナーと比較して気軽に依頼できる
* デザインサポーター制度

## アジャイル開発手法における監視システム開発効率化の取り組み
### 石田 瑛一
* https://drive.google.com/file/d/1imNXoqfQAbBGUDH1Y45fn1sVb1rgHjW6/view
* デプロイ作業の効率化が必要
  - 手順書でやってた
* Ansible、Gitlab CI/CD
  - 安定するまで2ヶ月くらいかかった

## スタートアップチームで学んだエンジニアの心構え
### 松木 久幸
* https://speakerdeck.com/matsu0228/the-attitude-of-the-engineer-who-learned-from-the-start-up-team
* 開発で一番難しいのは何を作るか決めること
  - 詳細まで認識を合わせる
  - 正解は誰にも判断できない
    - 常に変化が求められる
  - 価値向上のために「発散」も必要
* 仕事を楽しむこと
  - メンバーが主体的になるためにも、承認欲求を満たすことが大切

## NTTデータのトップ技術者育成！「技統本塾」のご紹介
### 小泉 鉄之祐
* 技術革新統括本部

## Amazon EKS上でのVNF開発奮闘記
### 篠原 健太
* https://speakerdeck.com/sinohara/amazon-eksshang-defalsevnfkai-fa-fen-dou-ji
* ネットワークの仮想化
* 閉域NW構築
  - AWSを閉域として構築できるか？
  - サブネットを分けて構築する
  - EKS v1.13から対応
  - マネージドのLBが外向きの通信に課題があったのでnginxを立てた

## Cisco ルータのログを Stackdriver に送って可視化してみた
### 田島 照久
* https://speakerdeck.com/tjmtrhs/cisco-rutafalseroguwo-stackdriver-nisong-tuteke-shi-hua-sitemita
* ログ基盤を作りたいわけではなく、可視化したログを見たいだけ
* stackdriverは外部のsyslogを直接受信できない
  - ルーターで処理すれば良い
* Ciscoのルーターで、Pythonが動かせる機種がある

## Closing Keynote
* 151/180人参加（速報値）
* 15人#1〜#4までに登壇した退職者
* もっと面白いエンジニアになる

