# mercari.go #9
* 2019/07/17 19:30-
* https://mercari.connpass.com/event/137488/

## @tottie	Gopher ライブドローイングのご説明


## @rerorero	protoactor-goでPregelを作った話
* グラフプロセッシングの話
* Map/Reduceの課題を解決するPregel（プリゲル）フレームワーク
* アクターモデル

## @knsh14	メルペイでの残高管理の話
* Balance Service
* gRPC, GKE, Spanner, Go
* 全体設計
  - クリーンアーキテクチャベース
  - Viewなし
    - Infra Layerで変換して返す
* トランザクション
  - UseCaseそうのInteractorで
  - 全体のロールバックが楽
* DB
  - 標準パッケージは使っていない
* APIの設計
  - 各種残高の増減機能
  - 種類にかかわらず同じインターフェースを提供したい
  - ロールバックしやすくしたい
  - 組み合わせのテストが大変
* 冪等性
  - どのAPIがリトライされても大丈夫なように作る
  - 参照系はあまり気にしていない
  - 取引IDでチェックしている
* データの整合性
  - 取引履歴が重要
    - 取引レコードから算出
    - 取引後の残高スナップショット
  - すべての処理が成功したときに履歴テーブルにコミットする

## @akkie	Readable code in Go
* コードを読みやすくするために
* 読みやすいコードとは
  - 他の人（本人含む）が最短時間で理解できるコード
* コメントに監督としての感想を書く
* コメントでコードをグループ分けする（テストコード）

## @tenntenn	The Go Playgroundをコマンドラインから扱う
* txtar（テキストアーカイブ）形式
  - `-- ファイル名 --` で区切る
  - playgroung上でタブ分けしてくれるchrome拡張あり
  - internalパッケージ

## @tottie	Gopher イラスト発表


## 
