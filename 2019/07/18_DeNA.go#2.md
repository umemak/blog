# DeNA.go #2
* 2019/07/18 19:30-
* https://dena.connpass.com/event/133957/

## @kiyotaka.nakashima / 新ゲームサーバ基盤TakashoでのGo言語活用事例の紹介 / ゲーム・エンターテインメント事業本部
* Sakasho
  - 共通ゲームサーバー（複数タイトルで相乗り）
  - プレイヤーデータの管理
  - 課金系
* Sakasyoの課題
  - 相乗りによる制約
  - 変更の影響大
* Takasho
  - Webサバーフレームワーク
  - ステートレスなAPI
  - 1サーバー1クライアント
  - GCP(GAE)前提(Terraformで構築)
  - 共通機能も提供
  - クライアント側はC#
  - サーバ側はGo
    - 少ない学習コストで高いパフォーマンスと安定性
* RPCサーバ
  - net/httpベース
  - gRPCの独自実装（GAEでgRPCがサポートされていなかった）
  - protoスキーマからコード生成
  - DBテーブルまわりもjsonで定義して生成

## @toku_bass /次世代タクシー配車サービス「MOV」におけるテスト事例紹介 / オートモーティブ事業本部


## @kurikei / DeSCヘルスケアにおけるGo活用事例の紹介 / DeSCヘルスケアサービス企画開発部


