---
title: "GitHubでpushできなかった"
date: "2022-08-20"
tags: ["github"]

---

VS Code再起動したタイミングで、git pushでエラーが出るようになった。

> Support for password authentication was removed on August 13, 2021. Please use a personal access token instead.

だいぶ前じゃないか、と思いつつ、PAT作ってやり直したら通った。

しばらくして次のpushしようとしたら、また同じエラー。

毎回PAT入れるのだるすぎるし、何でこのタイミングで出るようになったのか謎すぎる。

結局、VS Codeのターミナル再起動したら、聞かれなくなった。

