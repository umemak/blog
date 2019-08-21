---
author: "umemak"
date: 2019-07-17
title: Chromebookにgoの最新版をインストール
# tags: [ "chromebook", "go" ]
---

* apt-get だと最新版が入らないので、1.13に備えて最新版をインストールする手順を確認しておく。
* C101PAのOP1はARM系CPUなのでarm64用のファイルを使用する。
* C223NAはintel入ってるのでx86-64でいけるはず。

## 環境
* C101PA
* Linux(ベータ)

## 手順
* https://github.com/golang/go/wiki/ChromeOS を参考に進める
* https://golang.org/dl/ から go1.12.7.linux-arm64.tar.gz をダウンロード
  ```
  $ wget wget https://dl.google.com/go/go1.12.7.linux-arm64.tar.gz
  ```
* チェックサム確認
  ```
  $ sha256sum go1.12.7.linux-arm64.tar.gz 
  ```
* ファイル展開
  ```
  $ sudo tar xpvf go1.12.7.linux-arm64.tar.gz -C /usr/local
  ```
* バージョン確認
  ```
  $ /usr/local/go/bin/go version
  go version go1.12.7 linux/arm64
  ```
* ワークスペース作成
  ```
  $ sudo mkdir /usr/local/go/work
  ```
* パス設定
  ```
  $ export GOPATH="/usr/local/go/work"
  $ export PATH="${PATH}:/usr/local/go/bin:${GOPATH}/bin"
  ```
  一応、`~/.bash_profile`にも同等の内容を記載しておく
* 動作確認
  - ファイル作成
    ```
    $ sudo vim /usr/local/go/src/hello.go
    ```
  - ビルド
    ```
    $ go install hello
      can't load package: package hello: cannot find package "hello" in any of:
        /usr/local/go/src/hello (from $GOROOT)
        /usr/local/go/work/src/hello (from $GOPATH)
    ```
    エラー。。。
  - run
    ```
    $ go run /usr/local/go/src/hello.go 
    Hello, Chrome OS!
    ```
    とりあえず実行できたから良しとしておく。

