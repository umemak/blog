---
title: "GitHub Actions の MySQL で lower_case_table_names を変更する"
date: "2021-03-20"
tags: ["github", "actions", "mysql"]

---

[以前](../../2020/12/14_github_actions_mysql)書いた、GitHub Actionsでインストール済みMySQLを使う方法で起動したMySQLは、`lower_case_table_names`が`0`になっている（Linuxではこれがデフォルト）。

`lower_case_table_names`を`1`に変更したければ、`/etc/mysql/mysql.conf.d/mysqld.cnf`に`lower_case_table_names = 1`を追記して起動すれば良いだろうと気軽に考えてやってみたところ、MySQLが起動せず。

`/var/log/mysql/error.log`を確認したところ、
> [ERROR] [MY-011087] [Server] Different lower_case_table_names settings for server ('1') and data dictionary ('0').

とのエラー。
後から変更はできない、と。

そこで`mysqld --initialize`を使って初期化するところからワークフローに組み込む。

[ひとまずの完成物](https://github.com/umemak/githubactions_mysql_test/blob/main/.github/workflows/show_variables.yml)

- `mysqld.cnf`に追記
  ```
  echo 'lower_case_table_names = 1' | sudo tee -a /etc/mysql/mysql.conf.d/mysqld.cnf
  ```
- データディレクトリ再作成
  ```
  sudo rm -rf /var/lib/mysql
  sudo mkdir /var/lib/mysql
  sudo chown -R mysql:mysql /var/lib/mysql
  sudo chmod 750 /var/lib/mysql
  ```
- `mysqld initialize`
  ```
  sudo mysqld --defaults-file=/etc/mysql/my.cnf --initialize-insecure --lower_case_table_names=1
  ```
- MySQL起動
  ```
  sudo systemctl start mysql.service
  ```
- 結果確認
  ```
  mysql -u root -e "SHOW VARIABLES LIKE 'lower_case_table_names';"
  ```
  > Variable_name	Value
  > lower_case_table_names	1

ひとまずの、というのはrootのパスワード設定するとこまでたどり着かなかったので。
CI目的で使う分には問題ないかな、と。

