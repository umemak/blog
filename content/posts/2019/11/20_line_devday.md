---
title: "LINE DEVELOPER DAY 2019"
date: "2019-11-20"
tags: ["event", "line"]
---

https://linedevday.linecorp.com/jp/2019/

* 5回目の開催とのことですが、初参加です。

## 10:40- Keynote
### Euivin Park / LINE CTO
* LIFE with LINE
  - 今年だけで20以上のサービスをリリース
  - 金融系のサービスも多い
* LINE MINI App
  - 飲食店での例
* Natural Experience with AI
  - 2 Principles for Handling Data
    - To keep "Privacy Fitst"
    - To Avoid Data Silos
  - Unified Self-Service Data PlatformO
 * AI
   - 二千万次元
   - 受付の顔認証はiPadの機能を使っていた
   - 自分専用フォント
     - ５００文字？くらいで作れる
     - 鳥海さんの話ででていた基本文字みたいなの書くのかな？
     - APIを来場者に先行提供
  - Natural Language Processiong, STT/TSS
    - レストランの予約ができる音声合成AI
    - 今日から実店舗で稼働開始
  - Video Analysis
    - 動画を解析して字幕つける
    - まだ誤認識がある
* Data Platform
  - Self-Service Data Platform
  - 圧縮して390TB以上毎日蓄積される
  - データサイエンティストの本来の業務ができていないという課題
* Infra
  - Fast lifecycle infla
  - ピーク時1Tbpsのトラフィック
  - 4万台の物理サーバー
  - Private Cloud : Verda（OpenStack)
    - プライベートクラウドを持つ理由
      - 課題解決に対するイニシアチブ
      - オープンテクノロジーを選択できる
    - インフラのソフトウェア化
      - 不具合に対する対応が早い
      - CI/CDがまわせる
* セキュリティとプライバシー
  - Privacy First
  - Data GoVernance
    - Responsibility as a Platform
    - 専門チームによるチェック
  - LINE Account Hijack
    - ２段秋人相
    - 行動パターンを分析
    - 約２年で乗っ取り被害が０になった
  - Spam
    - MLを利用
    - Spammerの傾向を学習してフィルタパターンを自動更新
  - Fake News
  - Password Issue
    - fidoを利用
    - パスワードレスを進めていきたい
  - Tracsparency
    - 年２階透明性レポートを公開している
    - 今月15日からBug Bounty ProgramをHackeroneで開始
* Leading AI Technology
  - 

## 12:00- gRPC service development in private Kubernetes cluster
### Keiichiro Ui / LINE Development Team H Server Side Engineer
* LINE LIVEで利用
* なぜk8sか
  - トラフィックに対応するために手動でスケールする必要があった
  - オープンなエコシステムに乗ることができる
* どう使っているか
  - 内部ではgRPCで通信
  - 外部とはEnvoyで変換して通信
* gRPC-Web
  - https://github.com/grpc/grpc-web
* 社内の既存サービスとの連携
  - REST APIをgRPCで再定義
    - JSONをgRPCに変換する
* Istioを使わない理由
  - いくつかのコンポーネントはSpringで間に合う
  - パフォーマンスの問題
    - 1.89msが13.7msとか
* Databaseとの通信
  - MySQL with ACL
  - 事前にACLへの登録が必要
    - オートスケールとの相性が悪い
    - ACL Managerを作って回避
      - ノード追加をフックしてACLに登録（構想段階）
* Prometheus
  - 社内の時系列DBにメトリクスを蓄積して使う
  - メトリクス多い問題
    - 既存のプロジェクトからベストプラクティスを模索
* ログ収集
  - EFK(Elasticsearch+Fluentd+Kibana)
    - Fluentdを使った理由
      - Knativeの要件
      - K8sのaddonが参考になった
  - IMON（LINE社内開発）
    - 通知担当

## 13:40- Inside of Blog; Light and shadow of the service matured for 15 years and challenge chaos and legacy
### Takahiro Omori / LINE Development Team B
* livedoor blogとline blog
  - 15年の歴史があるのはlivedoorのほう
  - 70+開発者
  - 750+サーバー台数。うち200がdb。
  - 550+テーブル数
  - 43500+ファイル数
  - 3800+プログラムファイル（perl）
  - 410000+プログラム行数
  - サーバー移転
  - HTTPS化
    - サーバー移転終わらないと完了できない（闇）
* Document Not Found
  - デプロイ方法とか謎になっている
* Development Server Not Found
  - フローチャートで説明
* Too Many DBS Records
  - 300+??
  - 230が未使用
* Too Many Functions
* Perl
  - v5.8を使い続けている
  - mod_perlのせい
  - v5.16も使っている・・・混在
* MySQL
  - v4.0を使い続けている
  - いろいろ使えない機能が多い
* blogの特殊な事情
  - 文字コードセットの混在
  - これのせいで正規手順でMySQLのバージョンアップができない
* line blog
  - 2015年11月リリース
  - 当初はlivedoor blogのASPとして稼働
  - 2016年11月の一般公開で独立
  - livedoor blogからforkしたので、libedoorの闇も引き継いでいた
* Next 15 Years
  - 今担当しているサーブ素を１０年、１５年後に担当するメンバーが苦労しないよう心がける
  - 小さなことから

## 14:30- Technologies that support the distribution of LINE NEWS articles
### Daiki Inaba / LINE Development Team I Software engineer
* 68M MAU / 12B MPV
* PerlとJavaで動いている
* レコメンド配信はSpring(Java)で動いている
* MLと手動でのレコメンドを行っている
* MLのレコメンドは社内のDataLabで生成されたものを使っている
* 当初はMLのみでレコメンドしていた
* レコメンドデータのインポートの課題
  - １億人のデータを１時間ごとに
  - 並列処理（20スレッド*3台）で実施
* 初期実装の問題
  - スケーラビリティ
    - マッピングデータの形式変更
    - 記事IDではなく、ユーザーIDをキーにした
  - 運用コストが高い
    - ユーザーIDの抽出をCMSでできるようにした
    - 分析チームに依頼せず、属性フィルタで抽出する
* 今後
  - レコメンドクオリティ
  - リアルタイムフィードバック
    - 現在A/Bテスト中

## 15:30- Data Science drives improvement of LINE messenger
### Taro Takaguchi / LINE Data Science Team2 Senior Data Scientist / Manager
* Usrs First
* Data Driven
* Diverse Team
* In-house Development
* User Research
  - 対面インタビュー、インター別途アンケートなど
  - 数値モニタリング
* Plan & Development
  - 取得するログの定義など
* Test & Feedback
  - A/Bテスト
  - 結果の分析
* アプリの使われ方が多彩
* 単独のKPIが設定できない
* Core Value of LINE App
  - Closing the Distance
    - グループ機能
* グループ作成のフローでABSCESSテスト
  - 先にグループ名とアイコンを決める
  - 先にメンバーを決める
  - どちらも大差なかった
  - 招待メンバーの選択IFに問題があった
  - 最近話した相手を上位に表示
    - グループ作成完了までに時間が優位に短縮
  - グループ名設定とメンバー選択を同じ画面に
    - ネガティブ
* Data Science Tools
  - OASIS
    - 
  - LIBRA
    - データ抽出
  - LIBRA REPORT
    - テスト実施中のダッシュボード
  - R Shiny
    - ダッシュボードその２
  - Conflr
    - コンフルに共有するOSS

## 16:20- Introduction to XXE, SSRF, Insecure Deserialization
### Hiroshi Tokumaru / EG Secure Solutions Inc. President
* XML外部実体参照(XXE)
  - アップロードされたXMLを表示するパターン
    - ファイルパスを指定したらそれが表示されてしまう
    - URLを指定したらその内容が表示されてしまう
  - 対策
    - XMLの代わりにJSONを使う
    - 信頼できないXMLを解析しないことが大事
    - DTDを禁止する
    - PHPならlibxml2 2.9以降を使うとデフォルトで対策されている
    - RubyのREXMLは標準で対策済み
    - テストしてみるのが確実
* SSRF
  - 直接アクセスできない内部のサーバーに何らかの方法でアクセスする
* SSRF脆弱性とSSRF攻撃
  - 一般的に、脆弱性と攻撃手法は1対1の関係になっている
  - SSRFはそうではなく、脆弱性が多の関係になっている
* WAFに付与していたAIMロールの権限が強かった例
  - 本来不要なものまでついていた
* DNSリバインディング
  - DNS問い合わせの１回目と２回目で違う値を返す攻撃
  - gethostbynameしてからcurlするときなど
* 昨日、EC2でSSRF多層防御が実装されたアナウンスが出た
* 安全でないデシリアライゼーション
 - 対策
   - JSON形式にする
   - セッション変数を使う
   - 改ざんチェックを入れる

## 17:20- Cloud Native Challenges in Private Cloud with K8s, Knative
### Yuki Nishiwaki / LINE Verda Platform Development Team Manager


