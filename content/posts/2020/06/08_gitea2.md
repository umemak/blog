---
title: "続・CentOS6にgiteaをインストールする"
date: "2020-06-08"
tags: ["centos", "gitea"]
---

先日の続き。

CentOS6だと、ビルド済みバイナリは依存物のバージョンが合わず、自前ビルドはメモリが足りず。
古いGiteaのビルド済みバイナリなら動くが、やっぱり最新版使いたいし、ちょっとした機能追加もしたい。

そこで、バイナリ1本にまとめる方法をやめた（`TAGS="bindata"`を使わない）ところ、ビルドが通った。
ただ、おそらく開発環境向けの手順のため、設定ファイルなどがバイナリと同じ階層からたどれるところにある前提になっている。
ビルド時に`LDFLAG`環境変数を設定することで、書き換えることができる。

以下手順。

## ソースの取得とビルド
```
$ git clone https://github.com/go-gitea/gitea
$ cd gitea
$ git checkout v1.11.6
$ LDFLAGS="-X \"code.gitea.io/gitea/modules/setting.CustomPath=/var/lib/gitea\" -X \"code.gitea.io/gitea/modules/setting.AppWorkPath=/var/lib/gitea\"" make build
```

## 必要なファイルをコピー
```
sudo su
cp -r options /var/lib/gitea/
cp -r public /var/lib/gitea/
cp -r templates /var/lib/gitea/
cp gitea /usr/local/bin/gitea
```

## 起動
```
/usr/local/bin/gitea web -c /etc/gitea/app.ini -p 80
```


