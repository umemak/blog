---
title: "json2md"
date: "2022-05-29"
tags: ["JavaScript"]

---

JSONをマークダウンに変換するのは比較的簡単にできた。

mdmmlに組み込んでサンプル鳴らしてみたらなんかおかしい。

よく見ると`<`と`>`に囲まれたところが消えている。タグ扱いされてしまっているようだ。

JSONに保存するタイミングで`<`などが`&lt;`などに変換されているなぁ。
