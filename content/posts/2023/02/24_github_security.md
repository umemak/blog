---
title: "go.sumを消してみる"
date: "2023-02-24"
tags: ["go"]

---

GitHubのセキュリティメールが最近頻繁に来て、古いテスト用のリポジトリだったので、アラート対象になっている`go.sum`ファイルを消してみた。

これが正しい対応なのかわからないけど、`go.mod`で指定しているバージョンより古いもののsumが書かれていて、`go mod tidy`しても消えず、ファイルを消して`go mod tidy`したら復活するうえに、それがアラート対象になるのだから納得いかない。

nodeプロジェクトの`package-lock.json`でも同じようなことがあるので、こういう依存関係の管理ファイルは`.gitignore`してしまうのが良いのだろうか。
