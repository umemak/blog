---
title: "Amazon IVSプライベートチャネル"
date: "2022-07-08"
tags: ["aws"]

---

ストリームの再生にトークンが必要になる。

ほぼこのブログのやり方でできた。
- [[アップデート] Amazon Interactive Video Service で再生時の認証が行えるようになりました！ | DevelopersIO](https://dev.classmethod.jp/articles/update-amazon-interactive-video-service-auth/)

一点だけ、秘密鍵を Secrets Manager にアップロードのところでエラーになった。
cliのバージョンが変わって、コマンドに`--cli-binary-format raw-in-base64-out`オプションを指定する必要があるとのこと。
- [AWS Secrets Manager に AWS CLI で秘密鍵を格納したら Invalid base64 エラーが発生 - サーバーワークスエンジニアブログ](https://blog.serverworks.co.jp/cli-invalid-base64)

次は、S3に保存した動画を再生する方法を探る。
