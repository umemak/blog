---
title: "Amazon IVS+Amplify"
date: "2022-07-07"
tags: ["aws"]

---

IVSのサンプルアプリ（React製）をAmplifyにデプロイしてみた。

`npm run build`した`build`ディレクトリを丸ごとアップロードで。

jsとcssがHTTPコード301でファイル名の最後に`/`をつけたアドレスにリダイレクトされてエラーになっていたので、書き換えないようリダイレクト設定をしたら動いた。

IVSのストリーミングもOBSから送信できた。

次は[プライベートチャネルの設定](https://docs.aws.amazon.com/ja_jp/ivs/latest/userguide/private-channels.html)をやってみたい。
