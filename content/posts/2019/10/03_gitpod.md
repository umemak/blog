---
title: "Gitpod使ってみた"
date: "2019-10-03"
tags: ["git"]
---

https://www.gitpod.io/

GitHubのブラウザ版で、ブランチ切ったら編集できなくなったので、他にブラウザで使えるエディタないかなと検索して出てきたのがこれです。
GitHub連携するだけで使えるかと思ったらそうではなく、Gitpodにもアカウント作る必要があります。とはいえチェックボックス2つだけなのですぐ終わります。

コンテナの起動に少し時間がかかりました。
起動すると見慣れた画面がブラウザで表示される。VSCodeやんけ・・

オートコンプリートが邪魔なのでオフにしたいけれどどこで設定するのかすぐに見つからず。。
```
"editor.acceptSuggestionOnEnter": "off"
```
これでとりあえず回避できました。

ここまで書いたあと、そもそもの原因であったブランチでの編集ができるようになったので、もとのGitHubブラウザ編集に戻りました。

とはいえ、慣れた操作で色々できる可能性がありそうなので、もう少し使い込んでみたいと思います。