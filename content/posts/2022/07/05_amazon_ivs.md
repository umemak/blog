---
title: "Amazon IVSのサンプル"
date: "2022-07-05"
tags: ["aws"]

---

相変わらずエラーでIVSのチャットルームが作れない
> Your account is pending verification. Until the verification process is complete, you may not be able to carry out requests with this account. If you have questions, contact AWS Support.

仕方ないので、作れる方のアカウントで動作確認を進めることにした。

前に試したのと同じように、ap-northeast-1 でS3バケット作ってsam deployして、IVSチャットルームはus-east-1にした。
`Waiting to connect...`でつながらない。

サーバー側もus-east-1にしてやり直したら、無事動作確認できた。

本当は最初のときもus-east-1でやろうとして、s3バケット作るところでエラーになったのでap-northeast-1に変えたという経緯もあったのだけど。
コンソールから作ったらus-east-1でもエラーにならなかったので、そういうものなのかもしれない（Cloud Shellを起動したリージョンにしか作れないとか？）。

とりあえずサンプルで感触はつかめたので、カスタマイズして使っていきたい。
