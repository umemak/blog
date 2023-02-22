---
title: "GitHub Actionsのubuntuがdeprecatedでエラー"
date: "2023-02-22"
tags: []

---

昨日の更新がエラーになっていて、[add post · umemak/blog@a834cf9](https://github.com/umemak/blog/actions/runs/4231721048)見たら`ubuntu-18.04 environment is deprecated`とのこと。

[GitHub Actionsのubuntu-18.04がDeprecatedとなったので、ubuntu-latestへマイグレーションする](https://zenn.dev/azu/articles/5ef880c04560cb)
だいぶ前からアナウンスされていたらしい。

ということで、latestにして、ついでに`actions-hugo`と`actions-gh-pages`も最近のリリースに更新した。
