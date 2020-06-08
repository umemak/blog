---
title: "GiteaのデータベースをPostgreSQLにする"
date: "2020-06-08"
tags: ["gitea", "pgsql", "centos6"]
---

OSはCentOS6です。

https://qiita.com/hatayan1126/items/9b0d3be9c7ecdc207642 を参考に進めます。
この記事では9.6をインストールしていますが、せっかくなので最新の12を入れてみます。

## PostgreSQLのインストール
```
$ sudo su
# yum install https://download.postgresql.org/pub/repos/yum/reporpms/EL-6-x86_64/pgdg-redhat-repo-latest.noarch.rpm
# yum update
# yum install postgresql12-server
# rpm -qa | grep postgres
postgresql12-12.3-1PGDG.rhel6.x86_64
postgresql12-libs-12.3-1PGDG.rhel6.x86_64
postgresql12-server-12.3-1PGDG.rhel6.x86_64
# service postgresql-12 initdb
# cp /var/lib/pgsql/12/data/pg_hba.conf{,.bk}
# vim /var/lib/pgsql/12/data/pg_hba.conf
# diff /var/lib/pgsql/12/data/pg_hba.conf{.bk,}
80c80
< local   all             all                                     peer
---
> local   all             all                                     trust
82c82
< host    all             all             127.0.0.1/32            ident
---
> host    all             all             127.0.0.1/32            trust

# service postgresql-12 start
# chkconfig postgresql-12 --list
postgresql-12   0:off   1:off   2:off   3:off   4:off   5:off   6:off
# chkconfig postgresql-12 on
# chkconfig postgresql-12 --list
postgresql-12   0:off   1:off   2:on    3:on    4:on    5:on    6:off
```

## Gitea用設定
https://docs.gitea.io/en-us/database-prep/#postgresql の通り
```
$ sudo su
# vim /var/lib/pgsql/12/data/postgresql.conf
# service postgresql-12 restart
# su -c "psql" - postgres
postgres=# CREATE ROLE gitea WITH LOGIN PASSWORD 'gitea';
postgres=# CREATE DATABASE giteadb WITH OWNER gitea TEMPLATE template0 ENCODING UTF8 LC_COLLATE 'en_US.UTF-8' LC_CTYPE 'en_US.UTF-8';
postgres=# \q
# vim /var/lib/pgsql/12/data/pg_hba.conf
# service postgresql-12 restart
# psql -U gitea -d giteadb
giteadb=> \q
```

## Gitea設定書き換えて再起動
と思ったけど、DBのデータ移行面倒＆まだほとんど何も入っていないので、設定ファイル消して再インストールすることにする。
```
$ sudo su
# mv /etc/gitea/app.ini{,.bk}
# /usr/local/bin/gitea web -c /etc/gitea/app.ini -p 80
```

## Service化
https://github.com/go-gitea/gitea/blob/master/contrib/init/centos/gitea を`/etc/init.d/`にコピーして使う。
```
$ sudo su
# cd /etc/init.d/
# wget https://raw.githubusercontent.com/go-gitea/gitea/master/contrib/init/centos/gitea
# chmod +x gitea
# vim gitea
; GITEA_USERを変更する必要があるかもしれない
# service gitea start
# tail -f /var/lib/gitea/log/gitea.log
```
