---
title: "Oracle Cloudにインスタンス作成"
date: "2019-11-10"
tags: ["oci"]
---

Oracle Cloudに登録してから、なかなか無料インスタンス作成できずにいたけれど、今日試したら作れた。

sshログインしようとして、`Console Connections`作ってそこに出たコマンドコピペして、ログインアカウントとパスワードがわからずに詰む。

インスタンス作成時に特に指定してなかったけど、`opc`が割り当てられている。

で、再度ログインしようとするがパスワードが合わずに蹴られる。

別の手段。パプリックIPアドレスを割り当てて直接アクセス。したらできた。

パブリックIPアドレスもデフォルトでは付与されておらず、`Reserved Public IP`を取得してから割り当てる形式。

AWSと比べて、全体的にマネコンが不親切な感じ。

## dockerインストールまで
```
$ sudo yum update -y
$ sudo reboot
# 再ログイン
$ sudo yum install docker -y
$ docker -v
Docker version 18.09.8-ol, build 76804b7
$ sudo systemctl start docker
$ sudo usermod -aG docker opc
# 再ログイン
$ docker run hello-world
```
できた。
