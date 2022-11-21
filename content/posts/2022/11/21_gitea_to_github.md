---
title: "GiteaからGitHubへの移行"
date: "2022-11-21"
tags: ["gitea", "github"]

---

[Gitea](https://gitea.io/en-us/)のリポジトリをGitHubに移行してみる。

Giteaのほうは、バックアップのzipがある状態。

zipを展開して、リポジトリ（.git拡張子のディレクトリ）を`git clone`でローカルリポジトリとして取り込む。

移行先のGitHubリポジトリを作成して、`git remote set-url origin`でリモートリポジトリとして設定する。

`git push origin HEAD`でGitHubにアップ。

ファイルやコミット履歴はこれで移行できたが、IssueなどはGiteaのDBで管理しているので、この手順では移行できなかった。

バックアップデータの中にINSERTのSQLが含まれているので、それを見ながらIssue登録していったけど、多分もっと良い方法があると思う。。
