---
title: "Obsidian同期問題"
date: "2023-01-01"
tags: ["obsidian"]

---

Obsidian Self-hosted LiveSyncプラグイン を試してみた。

手始めに、ラズパイでサーバー起動しようとしたら、対応しているDockerイメージが無かった。

せっかくなので、OSを64bit版に入れなおして、動くようにした。

WindowsPCでクライアント側のプラグインを入れても設定が表示されず、無効にしてみたり他のプラグイン向こうにしたりしてみたけど、OS再起動したら直った。

で、接続しようとしたがうまくいかず。CORSエラーっぽいように見えるけど、よくわからない。

[Caddy - The Ultimate Server with Automatic HTTPS](https://caddyserver.com/)のことよくわからないままこれ以上進むのは難しそう。
