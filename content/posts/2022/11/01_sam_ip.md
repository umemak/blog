---
title: "AWS SSOの認証"
date: "2022-11-01"
tags: ["aws"]

---

[AWS IAM アイデンティティセンター (AWS SSO の後継)](https://aws.amazon.com/jp/iam/identity-center/)で新規ユーザーをワンタイムパスワード連携で作って、ログインしようとしたらできなかった。

設定したメールアドレスにメール認証を送って認証処理をしたら、ログインできるようになった。

そのあとも認証コードが設定メールアドレスに送られてきたりするので、メール使わずにユーザーを追加するのは無理っぽい。

CLIでできないかなーと思って調べたけど、そういうオプションはなさそう。

[create-user — AWS CLI 2.8.7 Command Reference](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/identitystore/create-user.html)
