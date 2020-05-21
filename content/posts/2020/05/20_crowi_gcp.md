---
title: "GCPでCrowiを動かす"
date: "2020-05-20"
tags: ["gcp"]
draft: true
---

## インスタンスの作成
名前：app01
リージョン：us-west1（オレゴン）
ゾーン：us-west1-b
マシンタイプ：f1-micro（1 vCPU、614MB メモリ）
ブートディスク：Debian GNU/Linux 10(buster)
ファイアウォール：HTTP、HTTPSを許可

## セットアップ
### 最新化
```
$ sudo apt update
$ sudo apt upgrade
$ sudo reboot
```

### dockerインストール
https://docs.docker.com/engine/install/debian/
```
$ sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common -y
$ curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
$ sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/debian \
   $(lsb_release -cs) \
   stable"
$ sudo apt-get update
$ sudo apt-get install docker-ce docker-ce-cli containerd.io -y
$ sudo docker run hello-world
$ sudo usermod -aG docker `whoami`
(再ログイン)
$ docker run hello-world
$ docker -v
Docker version 19.03.9, build 9d988398e7
```

### docker-composeインストール
https://docs.docker.com/compose/install/
```
$ sudo curl -L "https://github.com/docker/compose/releases/download/1.25.5/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
$ sudo chmod +x /usr/local/bin/docker-compose
$ docker-compose --version
docker-compose version 1.25.5, build 8a1c60f6
```

### crowiインストール
```
$ sudo apt install git -y
$ git clone https://github.com/crowi/crowi.git
$ cd crowi
$ docker-compse build
```
エラーになる。devDependenciesの`husky`で引っかかっているようなので、package.jsonから削除してみる。
→ディスク足りないエラーが発生。
　→デフォルトの10GBではなく、無料枠限度の30GBに変更する。
　　→`df`コマンドでの表示が変わらないので、rebootしてみる。
　　　→増えた。
　　　　→まだ`npm ci`のところでエラーになる。`Dockerfile`を編集して`npm install`に変更する。
　　　　　

