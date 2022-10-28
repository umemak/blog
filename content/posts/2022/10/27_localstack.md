---
title: "GoとLambda"
date: "2022-10-27"
tags: ["aws"]

---

aws-lambda-go-api-proxy でAPI作るとして、ローカルでのテスト環境どうするか問題。

[localstack/localstack: 💻 A fully functional local AWS cloud stack. Develop and test your cloud & Serverless apps offline!](https://github.com/localstack/localstack)を使うのが鉄板だと思うんだけど。

[API Gateway V2](https://docs.localstack.cloud/aws/apigatewayv2/)はPro版じゃないと使えない。

AWS環境にデプロイして動かすのが簡単なのかなぁ。
