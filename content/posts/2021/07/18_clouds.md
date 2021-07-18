---
title: "クラウドサービス比較"
date: "2021-07-18"
tags: ["aws", "azure", "gcp"]
---

AWSで構築しているシステムをAzureと並行稼働させることはできるのか？GCPは？という疑問を解消するために調べてみる。

## サービス比較

まずはAWS, Azure, GCPのサービス比較。

サービス名先頭の AWS, Amazon, Azure, Cloud(GCP) は省略。

### サーバーレスコンピューティング

AWS | Azure | GCP
---|---|---
[Lambda](https://aws.amazon.com/jp/lambda/) | [Functions](https://azure.microsoft.com/ja-jp/services/functions/) | [Functions](https://cloud.google.com/functions?hl=ja)
Java, Go, PowerShell, Node.js, C#, Python, Ruby  | C#, JavaScript(Node.js), F#, Java, PowerShell, Python, TypeScript | Node.js, Python, Go, Java, .NET Core(C#, F#), Ruby, PHP
[Lambda@Edge](https://aws.amazon.com/jp/lambda/edge/) |
Node.js, Python |
[CloudFront Functions](https://aws.amazon.com/cloudfront/) |
JavaScript |


### CDN

AWS | Azure | GCP
---|---|---
[CloudFront](https://aws.amazon.com/jp/cloudfront/) | [Content Delivery Network](https://azure.microsoft.com/ja-jp/services/cdn/) | [CDN](https://cloud.google.com/cdn?hl=ja)


### コードリポジトリ

AWS | Azure | GCP
---|---|---
[CodeCommit](https://aws.amazon.com/jp/codecommit/) | [Repos](https://azure.microsoft.com/ja-jp/services/devops/repos/) | [Source Repositories](https://cloud.google.com/source-repositories/?hl=ja)

### CI/CD

AWS | Azure | GCP
---|---|---
[CodePipeline](https://aws.amazon.com/jp/codepipeline/) | [Pipelines](https://azure.microsoft.com/ja-jp/services/devops/pipelines/) | [Build](https://cloud.google.com/build?hl=ja)

### IaC

AWS | Azure | GCP
---|---|---
[CloudFormation](https://aws.amazon.com/jp/cloudformation/) | [Resource Manager](https://azure.microsoft.com/ja-jp/features/resource-manager/) | [Deployment Manager](https://cloud.google.com/deployment-manager/docs?hl=ja)

- Azure Resource Managerを簡易操作するためのツール、Azure Building Blocksというものもある。

## 検討

- FaaSの対応言語が異なっている。共通で使えるのはJava、Node.js、C#、Python。
  - Lambda@Edgeも使っているなら、Node.jsかPythonしかない。
- CloudFormation の資産を Azure や GCP に移行できるのか
- [Terraform](https://www.terraform.io/)という選択肢もあり
- サーバーレス中心なら[serverless framework](https://www.serverless.com/)を検討してもよいかも

## 参考
- [AWS/Azure/GCPサービス比較 2021.07 - Qiita](https://qiita.com/hayao_k/items/906ac1fba9e239e08ae8)
- [3大クラウドAWS、Azure、GCPの機能を比較したら見えてきたサービスごとの違いと特徴とは？ | 株式会社トップゲート](https://www.topgate.co.jp/aws-azure-gcp)
- [エッジで爆速コード実行！CloudFront Functionsがリリースされました！ | DevelopersIO](https://dev.classmethod.jp/articles/amazon-cloudfront-functions-release/)
  - CloudFront FunctionsとLambda@Edgeの比較あり
- [Use AWS CodeCommit to mirror an Azure DevOps repository using an Azure DevOps pipeline | AWS DevOps Blog](https://aws.amazon.com/blogs/devops/use-aws-codecommit-to-mirror-an-azure-devops-repository-using-an-azure-devops-pipeline/)
  - AzureからAWSにミラーする方法。リポジトリを持っている側のFunctionsでgit mirrorする感じ。
- [CloudFront Functions の導入 – 任意の規模において低レイテンシーでコードをエッジで実行 | Amazon Web Services ブログ](https://aws.amazon.com/jp/blogs/news/introducing-cloudfront-functions-run-your-code-at-the-edge-with-low-latency-at-any-scale/)
- [GCP連載#10 Terraform ではなくCloud Deployment Manager を使ってみよう | フューチャー技術ブログ](https://future-architect.github.io/articles/20200219/)
- [Serverless Framework を使用したマルチクラウド ソリューション - Azure Example Scenarios | Microsoft Docs](https://docs.microsoft.com/ja-jp/azure/architecture/example-scenario/serverless/serverless-multicloud)
