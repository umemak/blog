---
title: "WebAssembly入門"
date: "2023-01-28"
tags: ["wasm"]

---

Goでクロスコンパイルしてwasmバイナリ作ってブラウザで動かすとか、Rustの本で紹介されているのとか知っているけど、実際動かしたことはなかったので試してみる。

- [WebAssembly - Wikipedia](https://ja.wikipedia.org/wiki/WebAssembly)
- [WebAssembly](https://webassembly.org/)

言語
- [I want to… - WebAssembly](https://webassembly.org/getting-started/developers-guide/)
意外と選択肢が少ない印象。その中にGoが入っているのも意外。

とりあえず、Goでやってみる。

- [GoのWASMがライブラリではなくアプリケーションであること - 株式会社カブク | 株式会社カブク](https://www.kabuku.co.jp/developers/annoying-go-wasm)
GoでやるのはRustと比べて面倒らしい。
そしてTinyGoなら面倒は解消されるらしい。

- [GoのコードをWebAssenblyにコンパイルしてブラウザ上でGoを実行する : ビジネスとIT活用に役立つ情報（株式会社アーティス）](https://www.asobou.co.jp/blog/web/go-webassembly)
これを見ながらやってみたが、書いてある通りにならなかった。
`Run`ボタン押すとエラー。
```text
wasm_exec.js:460 Uncaught (in promise) Error: Go.run: WebAssembly.Instance expected
    at globalThis.Go.run (wasm_exec.js:460:11)
    at run ((index):22:22)
    at HTMLButtonElement.onclick ((index):26:48)
```

- [Goで作ったロジックにWebUIをつけてGitHubページに公開する | フューチャー技術ブログ](https://future-architect.github.io/articles/20221024a/)
Next.jsとつなぐ例。

だいたいの流れはわかった。Goだと面倒なところがあるということも。

そしてwasmの使いどころがいまいち見えない。ブラウザのJSで速度の壁にぶつかったときに検討する感じかなぁ。
