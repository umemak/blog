---
title: "OracleCloudにSSH"
date: "2022-12-25"
tags: ["oci"]

---

OracleCloudの無料インスタンスにSSHしようとしてできない。

`Compute > Instances > Instance details`でPublic IP addressとUsernameは確認できる。

`Console connection`を開くと、`Launch Cloud Shell connection`と`Create local connection`が選択できて、Cloud Shellのほうを選ぶとブラウザ上でログインシェルが表示される、ユーザー`opc`で、パスワードがわからない。

local connectionのほうを選ぶと、鍵ペアがダウンロードできて、その秘密鍵を使ってログインしようとしても、Permission deniedエラーで入れない。

[WindowsからOracle Cloudの Linuxサーバにコンソール接続する | Oracle Cloud のことなら Cloudii（クラウディ）](https://cloudii.jp/news/blog/oracle-cloud/windows-to-oracle-linux-console/)を参考に、「Windowsのシリアル・コンソール接続のコピー」をPowershellで実行しても`Connection refused`でダメ。
せっかく普段使わないPuTTYもインストールしたのに。

せっかくPuTTYインストールしたので、ローカルで鍵ペア作って公開鍵を登録してログインするほうも試したけど、ダメだった。

何が入ってたか確認したかったけど、インスタンス作り直したほうが早いかもしれない。。
