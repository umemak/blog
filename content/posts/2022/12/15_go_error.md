---
title: "Goのエラーのラップ"
date: "2022-12-15"
tags: ["golang"]

---

[Goでスタイリッシュにエラーをラップする方法を学んだ - カミナシ エンジニアブログ](https://kaminashi-developer.hatenablog.jp/entry/2022/12/15/093000)を見て、なるほどと思った。

ただ、自分の場合はエラーメッセージに、エラーを返した関数なりメソッド名を入れたい派なので、一律同じになるこの方法は見送りかな、と。

```go
func hoge() error {
    err := Huga()
    if err != nil {
        return fmt.Errorf("Huga: %w", err)
    }
    return nil
}
```

こんな感じ。
