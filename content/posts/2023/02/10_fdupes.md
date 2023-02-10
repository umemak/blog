---
title: "fdupes"
date: "2023-02-10"
tags: []

---

外付けHDDから取り出したファイル、明らかに重複があるのできれいにしてから再待避したい。
ということで良いツールがないか探して、[adrianlopezroche/fdupes: FDUPES is a program for identifying or deleting duplicate files residing within specified directories.](https://github.com/adrianlopezroche/fdupes)というのがあるようで、WSLでもaptでインストールできた。

- [重複ファイルを削除（Ubuntu) - Qiita](https://qiita.com/fygar256/items/8a5bd5e2daea04c2b9a3)

実行してみると、ファイルリスト作成に結構時間がかかり、量は65万ファイルほど。

そのチェックが1ファイル1秒くらいかかっているので、終わるまでに65万秒、180時間もかかる計算。。

さすがに線形に時間がかかるとは思えないけど、先に手作業で刈り取ってからじゃないとダメかな。
