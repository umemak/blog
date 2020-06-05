---
title: "CentOS6にgiteaをインストールする"
date: "2020-06-05"
---

WikiはGitHubにも付いているのを思い出して、単独のWikiではなくGitHubクローンを試してみる。
GitLabとか重量系は最初からあきらめて、Goで書かれたシングルバイナリの軽量OSS、Giteaで挑戦。

VMはいつものGCP無料枠のやつ。
OSはCentOS6でディスクは30GB。

## MySQLのインストール
デフォルトだと5.1系しか入らないので、5.6系を https://qiita.com/Esfahan/items/83200c64de8d826677b5 を参考に入れる。
```
$ sudo yum -y install http://dev.mysql.com/get/mysql-community-release-el6-5.noarch.rpm
$ sudo yum -y install mysql mysql-devel mysql-server mysql-utilities
$ sudo mysql --version
$ sudo rpm -qa | grep mysql
```
サービスの起動時にエラーで落ちるので、 https://qiita.com/madaran0805/items/ae0532a7436e1c684e72 を参考にswapの設定をする。
```
$ sudo dd if=/dev/zero of=/swapfile bs=1M count=1024
$ sudo mkswap /swapfile
$ sudo swapon /swapfile
```
サービスの起動とrootパスワードの設定
```
$ sudo service mysqld start
$ sudo /usr/bin/mysql_secure_installation
```

## MySQLの設定
gitea用ユーザーの作成と権限周りの設定。
https://docs.gitea.io/en-us/database-prep/#mysql の local 用の手順で。
```
$ mysql -u root -p
mysql> SET old_passwords=0;
mysql> CREATE USER 'gitea' IDENTIFIED BY 'gitea';
mysql> CREATE DATABASE giteadb CHARACTER SET 'utf8mb4' COLLATE 'utf8mb4_unicode_ci';
mysql> GRANT ALL PRIVILEGES ON giteadb.* TO 'gitea';
mysql> FLUSH PRIVILEGES;
mysql> exit
$ mysql -u gitea -p giteadb
```

## giteaのインストール
https://docs.gitea.io/en-us/install-from-binary/ では`1.11.5`となっているが、現時点で最新が`1.11.6`なので読み替える。
gpg鍵の取り込みに失敗するので、shaで正当性の確認をする。
```
$ wget -O gitea https://dl.gitea.io/gitea/1.11.6/gitea-1.11.6-linux-amd64
$ wget https://dl.gitea.io/gitea/1.11.6/gitea-1.11.6-linux-amd64.sha256
$ cat gitea-1.11.6-linux-amd64.sha256
$ sha256sum gitea
```

## giteaの起動
gitをインストールする。
adduserで`--gecos`オプションが無効なので`--comment`に置き換える。`--group`を`--user-group`に置き換える。`--disabled-password`を削除する。
これはcentosだと`adduser`が`useradd`のシンボリックリンクつまり別コマンドのせい。
```
$ sudo yum install git
$ git --version
$ sudo su
# adduser \
   --system \
   --shell /bin/bash \
   --comment 'Git Version Control' \
   --user-group \
   --home /home/git \
   git
# mkdir -p /var/lib/gitea/{custom,data,log}
# chown -R git:git /var/lib/gitea/
# chmod -R 750 /var/lib/gitea/
# mkdir /etc/gitea
# chown root:git /etc/gitea
# chmod 770 /etc/gitea
# export GITEA_WORK_DIR=/var/lib/gitea/
# chmod +x gitea
# cp gitea /usr/local/bin/gitea
# GITEA_WORK_DIR=/var/lib/gitea/ /usr/local/bin/gitea web -c /etc/gitea/app.ini
FATAL: kernel too old
Aborted (core dumped)
```
えーーー
https://github.com/go-gitea/gitea/issues/4131 によると、`1.7.4`以前なら動くらしい。
やってみる。
```
# GITEA_WORK_DIR=/var/lib/gitea/ /usr/local/bin/gitea web -c /etc/gitea/app.ini
panic: Git version not supported. Requires version > 1.7.2

goroutine 1 [running]:
code.gitea.io/gitea/vendor/code.gitea.io/git.init.0()
        /go/src/code.gitea.io/gitea/vendor/code.gitea.io/git/git.go:79 +0x128
```
うーん。
https://www.softel.co.jp/blogs/tech/archives/6301 を参考に、gitのバージョンを上げる。
```
$ sudo su
# yum remove git
# yum install \
https://repo.ius.io/ius-release-el6.rpm \
https://dl.fedoraproject.org/pub/epel/epel-release-latest-6.noarch.rpm
# yum install git222
# git --version
```

```
# GITEA_WORK_DIR=/var/lib/gitea/ /usr/local/bin/gitea web -c /etc/gitea/app.ini -p 80
```
うごいた！

けど、最新バージョンではないのが何とも。。
とりあえず、Wikiのプレビューがないのは今回の用途だと痛いかなー。

## ソースからビルドしてみる
https://docs.gitea.io/en-us/install-from-source/
## goとnodejsのインストール
```
# yum install golang
# curl -sL https://rpm.nodesource.com/setup_10.x -o nodesource_setup.sh
# bash nodesource_setup.sh
# yum install nodejs
# go version
go version go1.13.6 linux/amd64
# node -v
v10.19.0
```
## ソースの取得とビルド実行
```
# git clone https://github.com/go-gitea/gitea
# cd gitea
# git checkout v1.11.6
# TAGS="bindata" make build
...
code.gitea.io/gitea/modules/public
# code.gitea.io/gitea/modules/public
fatal error: runtime: out of memory
...
```
だめか。。

## 結論
CentOS6で使うには、古いバージョンで我慢するしかない。
