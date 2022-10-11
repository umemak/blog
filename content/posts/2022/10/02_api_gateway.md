---
title: "OpenAPIとAPI Gateway"
date: "2022-10-02"
tags: ["aws", "OpenAPI"]

---

API GatewayにOpenAPIの定義を適用できる。
[OpenAPI を使用した REST API の設定 - Amazon API Gateway](https://docs.aws.amazon.com/ja_jp/apigateway/latest/developerguide/api-gateway-import-api.html)

API Gatewayの後ろにLambdaを使えば、EC2とかでGoのコンテナ動かすより安上がりになるのではないか？という思い付き。

この場合、APIサーバーはどういう構成で作るのかイメージがわかない。

現状は、openapi-generatorで生成したmodelやらを使ってやり取りしているが、lambdaだとエントリーポイントごとにmainパッケージを用意する？

1か所で受けてパラメータ見て振り分けとかしてたらAPI Gateway使う意味ないし、どうなんだろう？


