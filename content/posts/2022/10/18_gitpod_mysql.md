---
title: "GitpodでMySQLを使う"
date: "2022-10-18"
tags: ["Gitpod"]

---

Gitpod上で開発をするにあたって、DBが欲しかったのでMySQLが使えないか調べてみた。

[Workspace Image](https://www.gitpod.io/docs/configure/workspaces/workspace-image#configure-a-public-docker-image)にあるように、`.gitpod.yml`ファイルを作成してimageを指定すれば良いようだ。

```yaml
image: gitpod/workspace-mysql
```

ファイル作成してリポジトリにプッシュしてワークスペースを停止→スタートしてみる。

```bash
$ mysql -v
bash: mysql: command not found
```

再起動では反映されないようだ。

ワークスペースを停止した後、ダッシュボードでワークスペースを削除してから再度作成してみる。

```bash
$ mysql -v
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 8
Server version: 8.0.30-0ubuntu0.20.04.2 (Ubuntu)

Copyright (c) 2000, 2022, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Reading history-file /home/gitpod/.mysql_history
Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> \q
Writing history-file /home/gitpod/.mysql_history
Bye
```

できた。
