---
title: "Amazon IVSのサンプルを試してみた"
date: "2022-07-02"
tags: ["aws"]

---

[aws-samples/amazon-ivs-chat-web-demo: A demo web application that shows how to implement a basic video + chat application using the AWS serverless application model (SAM) and Javascript (React).](https://github.com/aws-samples/amazon-ivs-chat-web-demo)

これを試すにあたり、作ったものをまるごと削除できるようにAWS Organizationsで専用アカウント作成した。
ついでにAWS Single Sign-Onも設定してログインを集中管理できるようにした。

CloudShellで作業する。

```sh
$ git clone https://github.com/aws-samples/amazon-ivs-chat-web-demo.git
$ cd amazon-ivs-chat-web-demo/serverless/dependencies/nodejs
$ npm install
$ cd ../../
$ aws s3api create-bucket --bucket ivstestumemakhome123 --region ap-northeast-1 \
--create-bucket-configuration LocationConstraint=ap-northeast-1
$ sam package --template-file template.yaml \
  --s3-bucket ivstestumemakhome123 \
  --output-template-file output.yaml
$ sam deploy --template-file ./output.yaml \
--stack-name ivstest \
--capabilities CAPABILITY_IAM \
--region ap-northeast-1
```

```sh
$ cd ../web-ui/
$ vim src/config.js
```
`CHAT_ROOM_ID`を取得するために、コンソールからチャットルームを作成しようとしたら東京リージョンでは選択できなかった。
us-east-1（バージニア北部）にした。

> Your account is pending verification. Until the verification process is complete, you may not be able to carry out requests with this account. If you have questions, contact AWS Support.

アカウント作ったばかりだから？よくわからない。

昔に作った別のアカウントで試したら通ったので、出来立てのアカウントではダメみたい。

せっかくなので、CHAT_ROOM_IDをその別アカウントで作ったものにして動くかやってみる。

```sh
$ npm install
$ npm start
```
CloudShellだとlocalhost:3000にブラウザからアクセスできない？か。web-uiはローカルPCで動かしてみる。

```sh
$ git clone https://github.com/aws-samples/amazon-ivs-chat-web-demo.git
$ cd amazon-ivs-chat-web-demo/web-ui/
$ vim src/config.js
$ npm install
$ npm start
```

動画は再生されているけど、チャットが`Waiting to connect...`で止まってしまっている。
authで500エラーが返ってきているみたいなので、一晩待ってからチャットルーム再作成してみましょう。
