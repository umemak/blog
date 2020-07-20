---
title: "WSL2にbrewをつかってnodejsのインストールをする"
date: "2020-07-20"
tags: ["wsl"]
---

Node.jsのバージョン管理したくなったので。

## Homebrewのインストール
https://brew.sh/index_ja にしたがって。
```
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
$ sudo apt-get install build-essential
$ echo 'eval $(/home/linuxbrew/.linuxbrew/bin/brew shellenv)' >> /home/`whoami`/.profile
$ eval $(/home/linuxbrew/.linuxbrew/bin/brew shellenv)
$ brew --version
Homebrew 2.4.8
Homebrew/linuxbrew-core (git revision 09353; last commit 2020-07-19)
```

## インストール済みnodejsパッケージの削除
aptで入れていたnodejsを削除。
```
$ sudo apt remove nodejs
```

## nodebrewのインストール
```
$ brew install nodebrew
```

## nodejsのインストール
```
$ nodebrew install v12.18.2
Fetching: https://nodejs.org/dist/v12.18.2/node-v12.18.2-linux-x64.tar.gz
Warning: Failed to create the file
Warning: /home/umemak/.nodebrew/src/v12.18.2/node-v12.18.2-linux-x64.tar.gz:
Warning: No such file or directory
curl: (23) Failed writing body (0 != 978)

download failed: https://nodejs.org/dist/v12.18.2/node-v12.18.2-linux-x64.tar.gz
```
ディレクトリ掘ってみる
```
$ mkdir -p ~/.nodebrew/src
$ nodebrew install v12.18.2
Fetching: https://nodejs.org/dist/v12.18.2/node-v12.18.2-linux-x64.tar.gz
################################################################################################################# 100.0%
Installed successfully
```
使用バージョン指定
```
$ nodebrew use v12.18.2
use v12.18.2
```
バージョン確認
```
$ node -v

Command 'node' not found, but can be installed with:

sudo apt install nodejs
```
あれ。。
```
$ ~/.nodebrew/current/bin/node -v
v12.18.2
```
PATHが通ってない。
```
$ vim ~/.profile
export PATH=$HOME/.nodebrew/current/bin:$PATH
$ source ~/.profile
$ node -v
v12.18.2
```
できた。
