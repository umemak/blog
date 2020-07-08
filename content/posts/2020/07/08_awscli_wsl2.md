---
title: "WSL2でAWS CLIを使ってS3のフォルダ名を変更する"
date: "2020-07-08"
tags: ["wsl", "aws", "docker"]
---

S3って、マネジメントコンソールからフォルダ名の変更ってできないんですね。。

[こちら](https://blog.goo.ne.jp/nakano-tomofumi/e/78ed6b49344715a89a9fdebeba8a8dd2)を参考に。

SurfaceにしてからAWS CLIインストールしてなかったし、せっかくなのでWLS2のUbuntuでやってみます。

公式の[Docker版](https://docs.aws.amazon.com/ja_jp/cli/latest/userguide/install-cliv2-docker.html)でインストール（というほどのことでもないですが）。
```
$ docker run --rm -it amazon/aws-cli --version
aws-cli/2.0.29 Python/3.7.3 Linux/4.19.104-microsoft-standard botocore/2.0.0dev33
```

認証情報入れる。
IAMでアクセスキーを取得して、configureコマンドで設定。
```
$ docker run --rm -ti -v ~/.aws:/root/.aws amazon/aws-cli configure
```

動作確認
```
$ docker run --rm -ti -v ~/.aws:/root/.aws amazon/aws-cli s3 ls
```
バケット一覧が表示される。OK。

リネーム実行
```
$ docker run --rm -ti -v ~/.aws:/root/.aws amazon/aws-cli s3 mv "s3://<バケット名>/<変更前>" "s3://<バケット名>/<変更後>" --recursive
```
フォルダ名にスペースが入っていたので、ダブルコーテーションで囲っています。

大した手間ではないけれど、やっぱりブラウザからできたほうが便利だと思う。
