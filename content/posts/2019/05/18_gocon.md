---
author: "umemak"
date: 2019-05-18
title: Go Conference 2019 Spring
# tags: [ "go", "event" ]
---

* https://gocon.jp/
* 2019/05/18(土) 10:00-19:00
* リクルートライフスタイル

## まとめ
* エラーハンドリングはまだ各社試行錯誤している印象
* コンテナやるならGoわかると便利
* 英語もっとわかるようにならないとだめだ

## Keynote
* パッケージのプロキシとDBの話
* 英語だったので言ってること半分もわからなかった

## B1 (S): How a “not the greatest engineer” achieved his first contribution to Go
* https://speakerdeck.com/yotak/how-a-not-the-greatest-engineer-became-a-go-contributor
* コントリビュートしようぜって話
* これも英語での発表だった

## B2 (S): エラー設計について/Designing Errors
* エラーの分類とどう処理するか

## H3 (S): 標準パッケージのみで大量のPNG画像をいかに高速に処理するか
* https://go-talks.appspot.com/github.com/cia-rana/go-png-bench/doc/slide/gocon2019.slide#1
* pprofで計測し、ボトルネックを絞り込んでから対策を打つことが大事

## A4 (S): Design considerations for container-based Go applications
* https://speakerdeck.com/hgsgtk/design-considerations-for-container-based-go-application
* 開始時間ギリギリに行ったらスクリーン見える場所が確保できなかった
* 12factorsに加えて、pivotalとRedhatにもそういうのがあるらしい
  - [Beyond the Twelve-Factor App](https://content.pivotal.io/blog/beyond-the-twelve-factor-app)
  - [コンテナベース・アプリケーションの設計原則](https://www.redhat.com/cms/managed-files/cl-cloud-native-container-design-whitepaper-f8808kc-201710-a4-ja.pdf)

## H5 (L): Writing Go Analyses with go/analysis (from Go Team)
* https://github.com/matloob/analysistalk/blob/master/presentations/tokyo.key
* 英語に加えて、そもそもの課題感が把握できてなかったので理解度低
* 発表中にMacの電池が切れたりカーネルパニック起こしたり

## H6 (S): Dive into Buildkit LLB with Go
* https://speakerdeck.com/po3rin/dive-into-buildkit-llb-with-go
* Dockerfileの解析まわり
* 使いこなせれば夢が広がりそう

## H8 (L): Building Modules Discovery (from Go Team)
* 使いたいモジュールを探して比較検討しての手間を解消するサービス
* 公式？

