---
title: "urfave/cliその2"
date: "2023-03-26"
tags: ["go"]

---

v2がエラーになる件、Codespacesでも問題なかった。いよいよWindowsの問題な気がしてきた。

→上位ディレクトリの`go.work`に追加したら、`go run`時のエラーは解消した。

VS Code再起動したら、ソースのエラー表示も消えた。

`go.work`に原因あるとかわかりにくすぎる。。
