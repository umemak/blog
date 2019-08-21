---
author: "umemak"
date: 2019-07-30
title: Chromebook(C101PA)にVSCodeをインストールする２
# tags: [ "chromebook", "vscode" ]
---

昨日は空き容量が足りなくなってあきらめたので、今回は何もない状態からやってみる。

## インストールしながら空き容量をチェック
  * Linuxを再インストールした直後
    ```
    $ df -h
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/vdb        5.5G  1.3G  3.9G  25% /
    ```

  * VSCodeのインストールしてdebファイル削除したあと
    ```
    $ df -h
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/vdb        5.5G  1.8G  3.4G  34% /
    ```

  * mozcインストール後
    ```
    $ df -h
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/vdb        5.5G  2.1G  3.1G  42% /
    ```

  * fonts-notoインストール後
    ```
    $ df -h
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/vdb        5.5G  2.2G  3.0G  42% /
    ```

  * 1GB程度消費する模様

## https://qiita.com/kukita/items/b673bf6eba2cc91fc545 に沿ってGoもインストールする
  * goインストール後
    ```
    $ df -h
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/vdb        5.5G  2.6G  2.7G  50% /
    ```

  * VSCode拡張機能などインストール後
    ```
    $ df -h
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/vdb        5.5G  2.8G  2.5G  53% /
    ```

## dockerインストール
  * [公式の手順](https://docs.docker.com/install/linux/docker-ce/debian/#install-using-the-repository)で実施
    ```
    $ df -h
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/vdb        5.5G  3.2G  2.0G  62% /
    ```
  * VSCodeのDocker拡張を使うには、sudoいらなくする設定と再ログインが必要。
    ```
    $ sudo groupadd docker
    $ sudo usermod -aG docker $USER
    ```

## まとめ
* VSCode使うには1GB以上の空き領域が必要。
* 先人の知恵に感謝。
* 元記事にもあるように、dlvはインストールできない。arm用パッケージがないらしい。
* dlvがないとデバッグ実行ができない。
* Remote Development拡張入れようとしたら、本体のバージョンが足りていなくてできなかった。
* 容量が足りなくなったのは、不要なコンテナイメージが残っていたのかもしれない。
