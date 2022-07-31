---
title: "VS Codeでブラウザ表示したい"
date: "2022-08-01"
tags: ["VS Code"]

---

VS Codeとブラウザを行き来するのが面倒なので、VS Code内でブラウザ表示できれば良いのでは？と思い方法を探してみた。

[デバッグ作業が快適に！VS Codeにブラウザのプレビュー機能を加える機能拡張 -Browser Preview for VS Code | コリス](https://coliss.com/articles/build-websites/operation/work/browser-preview-for-vscode.html)

これでいけるじゃん、ってインストールしようとしたら、Deprecated と書かれていて、代わりに[Live Preview - Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.live-server)を使うよう誘導されていた。

Live Preview入れてみたけど、これ拡張機能のサーバーしかプレビューさせてくれない（他のポートやサイトが開けない）ようで、思ってた使い方ができない。

他にないか探してみて、[VS Browser - Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=Phu1237.vs-browser)を入れてみた。

良さそうだけど、動作がちょっと不安定かな。ページが開けたり開けなかったりする。
