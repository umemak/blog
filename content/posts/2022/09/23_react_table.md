---
title: "Reactでテーブルを使う3"
date: "2022-09-23"
tags: ["react"]

---

Tanstack Table続き。

とりあえず、公式のサンプルのように実装したら、動いた。

APIから取得したデータを使おうとすると、エラーになる。
useEffectを外してみたら、APIがすごい勢いでたたかれ続けた。
useEffectを戻したら、エラー出ずに表示された。

？？？

APIサーバーを停止してみると、またエラーになった。

つまりAPIリクエストのエラー時の処理がうまく書けていないらしい。

エラー時に
```js
return <div>Error: {error}</div>;
```
としていたところを
```js
return <div>Error: {error.message}</div>;
```
にしたところ、解消できた。

解消できたけど、VS Codeでエラー表示`プロパティ 'message' は型 'never' に存在しません。ts(2339)`になるのが気になる。。

あと、APIサーバーのログを見ると、2回リクエストが来ているのが気になる。
