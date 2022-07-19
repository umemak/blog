---
title: "Goのエラー処理"
date: "2022-07-19"
tags: ["go"]

---

`fmt.Errorf("～～: %w", err)`の書き方にルールあるのかな、と思って調べたら、先人の記事があった。

- [fmt.Errorfのメッセージについての調査と、linterとしての実装について | CyberAgent Developers Blog](https://developers.cyberagent.co.jp/blog/archives/36253/)

いつもその時の雰囲気で書いていたので、こういったルールで揃えられるのは良い。

もうひとつ、`template.Execute`でエラーになったときに、どうするべきなのかという疑問。これも解決されていた。

- [How to handle template execution errors in Go](https://freshman.tech/snippets/go/template-execution-error/)

`bytes.Buffer`にいったん入れたら良い。なるほど。

二つ賢くなった。
