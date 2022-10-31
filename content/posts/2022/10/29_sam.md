---
title: "SAM入門"
date: "2022-10-29"
tags: ["aws", "sam"]

---

SAM使ったらいい感じにLambdaできそうなので、やってみる。

[Installing the AWS SAM CLI - AWS Serverless Application Model](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-install.html)
からインストーラーをダウンロードして、インストール。

VS Codeのターミナルからsamが実行できない（コマンドプロンプトからだとできる）。

いきなり躓いてやる気が。。

とりあえず、Windows版をアンインストールして、WSL2でLinux版をインストール。

awsコマンドもインストール。
[AWS CLI の最新バージョンをインストールまたは更新します。 - AWS Command Line Interface](https://docs.aws.amazon.com/ja_jp/cli/latest/userguide/getting-started-install.html#getting-started-install-instructions)

sam実行
```sh
$ sam init --runtime go1.x
$ cd sam-app
$ sam local start-api
```
http://127.0.0.1:3000/hello にアクセスしてIPアドレスが表示された。OK。

IAMユーザーsamを作成して、`aws configure --profile sam` でキー設定。

デプロイ
```sh
$ sam deploy --guided --profile sam

Configuring SAM deploy
======================

        Looking for config file [samconfig.toml] :  Not found

        Setting default arguments for 'sam deploy'
        =========================================
        Stack Name [sam-app]:
        AWS Region [us-east-1]: ap-northeast-1
        #Shows you resources changes to be deployed and require a 'Y' to initiate deploy
        Confirm changes before deploy [y/N]:
        #SAM needs permission to be able to create roles to connect to the resources in your template
        Allow SAM CLI IAM role creation [Y/n]:
        #Preserves the state of previously provisioned resources when an operation fails
        Disable rollback [y/N]:
        HelloWorldFunction may not have authorization defined, Is this okay? [y/N]: y
        Save arguments to configuration file [Y/n]:
        SAM configuration file [samconfig.toml]:
        SAM configuration environment [default]:

        Looking for resources needed for deployment:
        Creating the required resources...
        Successfully created!
```
出力の中にあるURLにアクセスして、IPアドレスが表示された。

作られたものは、template.yamlを見ると`HelloWorldAPI`と`HelloWorldFunction`と`HelloWorldFunctionIamRole`の3つとこれらをまとめるCloudFormationと、`aws-sam-cli-managed-default`というのがあった。

main.goを編集して、`make`、`sam deploy --profile sam`で更新された。

削除
```sh
$ sam delete --profile sam
        Are you sure you want to delete the stack sam-app in the region ap-northeast-1 ? [y/N]: y
        Are you sure you want to delete the folder sam-app in S3 which contains the artifacts? [y/N]: y
        - Deleting S3 object with key sam-app/c76671a85d3c296ac1bd69c32352798f
        - Deleting S3 object with key sam-app/1753ad35ae8d1d0bcddf744d77f7c03f.template
        - Deleting S3 object with key sam-app/59eb8f4eeaf8324a52fd7d8ed8741599
        - Deleting S3 object with key sam-app/a848bcfd2d0f1d832ad1ce31edca1e2f.template
        - Deleting Cloudformation stack sam-app

Deleted successfully
```

なんかできそうな気がしてきた。
