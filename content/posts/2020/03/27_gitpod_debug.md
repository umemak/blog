---
title: "GitpodでReactアプリのデバッグをする（未完）"
date: "2020-03-27"
tags: ["gitpod"]
---

Next.jsの動作がよくわからないので、デバックモードで追いかけようとしたところ、設定に躓いたのでメモ。

https://marketplace.visualstudio.com/items?itemName=msjsdiag.debugger-for-chrome
ここの`Download Extension`でvsixファイルをダウンロードする。

GitpodのExtensions(Beta)サイドメニューを開いて、`Drag & drop VS Code extensions (*.vsix) to install`のところにダウンロードしたファイルを入れるとインストールされる。

https://code.visualstudio.com/docs/nodejs/reactjs-tutorial#_debugging-react
この通りに`launch.json`を作成して、実行。
・・・起動しない。GitpodのコンテナにChromeインストールしてないからそりゃそうだね。

`launch`じゃなくて`attach`にしてみる。
・・・デバッグ用のポートが空いてないエラー。
あれ。ChromebookのChromeってデバッグポート開けて起動ってどうやるんだろう。。
