---
title: "DockerでSpring Boot"
date: "2023-01-19"
tags: ["docker", "Spring Boot"]

---

[Docker で Spring Boot - 公式サンプルコード](https://spring.pleiades.io/guides/gs/spring-boot-docker/)を見ながらやってみた。

ローカルにJDKが入っていなかったので、Dockerでビルドしてみたところ、うまく動かず。。

リンクされている[Spring Initializr](https://start.spring.io/#!type=gradle-project&language=java&platformVersion=2.5.5&packaging=jar&jvmVersion=11&groupId=com.example&artifactId=spring-boot-docker&name=spring-boot-docker&description=Demo%20project%20for%20Spring%20Boot&packageName=com.example.spring-boot-docker&dependencies=web)で、Javaが11を選択されていたので、Dockerイメージも11を使ったのだが、Spring Initializrとイメージを17にしたら、通った。
[英語版](https://spring.io/guides/gs/spring-boot-docker/)のリンクは何もオプションパラメータがついていなくて最初から17が選択されていたので、日本語版の変更が追いついていないだけなのかもしれない。

そして日本語版を管理しているリポジトリが見つからないので修正リクエストも出せない。残念。

→<https://github.com/cypher256/pleiades.io>でissue管理している様子。
