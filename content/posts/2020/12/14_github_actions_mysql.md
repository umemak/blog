---
title: "GitHub Actions で MySQL を使う"
date: "2020-12-14"
tags: ["github", "actions", "mysql"]
---

GitHub ActionsでMySQLを使ったCIを回したかった。

ググると、servicesでmysqlコンテナを立ち上げる方法がヒットしたが、コンテナの起動に45秒くらいかかっていて、ちょっと長いなー、と。
そこでmysqlをインストールしたらどうなんだろうと思い、そういえばmysqlコマンドラインツールは最初から入っていたけど、他に何入っているんだろうと調べたら、MySQL Serverもインストールされているのを見つけた。
https://github.com/actions/virtual-environments/blob/main/images/linux/Ubuntu2004-README.md

デフォルトでは起動していないので、使う前に起動させる必要がある。
```yaml
- name: start mysql
  run: sudo systemctl start mysql.service
```
