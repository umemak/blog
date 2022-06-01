---
title: "Firebase用デプロイサーバーを作る"
date: "2020-06-11"
tags: ["linux", "firebase", "gitea"]
---

SourceRepositoriesで管理して、CloudBuildでFirebase HostingにデプロイしているGatsbyプロジェクトを、SourceRepositoryとCloudBuildを使わずに実現してみる。
GiteaがCentOS6で動くようになったので、SourceRepository部分は置き換えられる。
CloudBuildをWebhookでスクリプト呼び出してやろうとしたところ、CentOS6ではGatsbyのビルドができない（古すぎる。。）
仕方ないので、ビルドサーバーを別で用意する。

新規で建てるのでOSはDebianでいってみる。環境はいつものGCPインスタンス無料枠で。

## パッケージインストール
```
$ sudo su
# apt update
# apt upgrade
# apt install git nginx unzip
# exit
$ curl -fsSL https://deno.land/x/install/install.sh | sh
$ vim ~/.bash_profile
$ source ~/.bash_profile
$ deno --version
deno 1.0.5
v8 8.4.300
typescript 3.9.2
$ git --version
git version 2.20.1
$ nginx -v
nginx version: nginx/1.14.2
```

## 受け口の作成
```
$ vim denoserver.ts
```
```
import { serve } from "https://deno.land/std@0.56.0/http/server.ts";
const s = serve({ port: 8000 });
console.log("http://localhost:8000/");
for await (const req of s) {
  req.respond({ body: "Hello World\n" });
}
```
```
$ deno run --allow-net denoserver.ts
```
```
$ curl localhost:8000
Hello World
```

## プロキシ設定
```
$ sudo vim /etc/nginx/conf.d/deno.conf
```
```
server {
    listen      80 default;
    server_name  localhost;
    location / {
        proxy_pass http://localhost:8000;
    }
}
```
```
$ sudo rm /etc/nginx/sites-enabled/default 
$ sudo service nginx restart
$ deno run --allow-net denoserver.ts
```
※ブラウザで表示できることを確認する。
