---
title: "マークダウンエディター選び"
date: "2022-05-08"
tags: ["JavaScript", "editor"]

---

マークダウン部分の入力に使うライブラリを探す。

`markdown` `WYSIWYG`をキーワードにnpmを[検索](https://www.npmjs.com/search?q=markdown%20WYSIWYG)した結果、

- [outline/rich-markdown-editor: The open source React and Prosemirror based markdown editor that powers Outline. Want to try it out? Create an account:](https://github.com/outline/rich-markdown-editor)
  - 良さそうだけどArchivedになっててメンテナンスされてない？
- [nhn/tui.editor: 🍞📝 Markdown WYSIWYG Editor. GFM Standard + Chart & UML Extensible.](https://github.com/nhn/tui.editor)
  - プレビュー形式ではなくて、直接編集したい
- [codex-team/editor.js: A block-styled editor with clean JSON output](https://github.com/codex-team/editor.js)
  - 良さそう
- [Saul-Mirone/milkdown: 🍼 Plugin driven WYSIWYG markdown editor framework.](https://github.com/Saul-Mirone/milkdown)
  - テーブルの行列追加がワンクリックでできれば

ということで、editor.jsを試してみようと思う。

→保存するときの形式がマークダウンではなくてJSONだった。よく見たらタイトルにもそう書いてある。。

次、milkdownを試してみる。こっちはmarkdown editorと書いてあるからきっと大丈夫・・のはず。

→なんかHTMLのJSからお手軽に呼べる奴じゃない感じ。

詰んだ。。
