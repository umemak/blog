---
title: "runnでgRPCのテスト"
date: "2022-11-17"
tags: ["go", "gRPC"]

---

gRPCサーバーをテストするのに、[fullstorydev/grpcurl: Like cURL, but for gRPC: Command-line tool for interacting with gRPC servers](https://github.com/fullstorydev/grpcurl)を使っていたのだけど、自動化するのに良いものはないかと探して、[k1LoW/runn: runn is a package/tool for running operations following a scenario.](https://github.com/k1LoW/runn)を試してみた。

go testから使うのは何となくできたような気がするけど、runnコマンドで実行するのがうまくいかない。

go testから使うのもだいぶハマって、`tls: false`を入れないとポート番号80以外で起動したときに常にTLS接続になって、応答がなくなってしまう。

うまくいけばいい感じに使えそうな気がするので、もう少し深堀してみたい。
