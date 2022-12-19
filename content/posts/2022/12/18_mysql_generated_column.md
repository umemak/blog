---
title: "MySQLのGenerated Column"
date: "2022-12-18"
tags: ["MySQL"]

---

MySQLのGenerated Columnというものを知った。

- [MySQL :: MySQL 8.0 リファレンスマニュアル :: 13.1.20.8 CREATE TABLE および生成されるカラム](https://dev.mysql.com/doc/refman/8.0/ja/create-table-generated-columns.html)
- [第150回　Generated Columnを利用してみる | gihyo.jp](https://gihyo.jp/dev/serial/01/mysql-road-construction-news/0150)
- [MySQLのGenerated Columnsまとめ with Rails - Qiita](https://qiita.com/naka_kyon/items/f3e19ab7a6275ab394bf)
- [MySQL の Generated Columns のキャッチアップ - Please Sleep](https://please-sleep.cou929.nu/mysql-generated-columns.html)
- [JSON型にindexも！MySQL 5.7のGenerated Columnsの可能性について探る - UUUMエンジニアブログ](https://system.blog.uuum.jp/entry/mysql-generated-columns)

MySQL5.7.6から追加された機能とのことで、リリースされたのは2015年。だいぶ前だ。。

- [MySQL :: MySQL 5.7 Release Notes :: Changes in MySQL 5.7.6 (2015-03-09, Milestone 16)](https://dev.mysql.com/doc/relnotes/mysql/5.7/en/news-5-7-6.html)

たしかに、何やら便利そうではあるが、使いどころは限定される気がする。
他のテーブルも参照できれば、、ってそれはVIEWだ。
