---
title: "GoとLambda"
date: "2022-10-25"
tags: ["aws"]

---

昨日、API GW+Lambdaの可能性について調べたとき、aws-lambda-go-api-proxy というものを見つけた。

[awslabs/aws-lambda-go-api-proxy: lambda-go-api-proxy makes it easy to port APIs written with Go frameworks such as Gin (https://gin-gonic.github.io/gin/ ) to AWS Lambda and Amazon API Gateway.](https://github.com/awslabs/aws-lambda-go-api-proxy)

良さそうだけど、PRが結構たまっているなーと思い、よく見てみると

[Deprecation in favor of Lambda Web Adapter · Issue #143 · awslabs/aws-lambda-go-api-proxy](https://github.com/awslabs/aws-lambda-go-api-proxy/issues/143)

とのことで

[awslabs/aws-lambda-web-adapter: Run web applications on AWS Lambda](https://github.com/awslabs/aws-lambda-web-adapter)

の使用を勧められていた。

が、上記Issueでコンテナだと起動が遅いという指摘が出ている。

とりあえずchiのV2対応マージしてくれれば、proxyの方で問題ないんだけどなー・・
