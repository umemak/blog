---
title: "Windows10の設定"
date: "2020-03-30"
tags: ["windows"]
---

Chromebookでの作業に限界が見えたので、WindowsPCを調達しました。
自分で買うのは初めてのDell。

OSはWindows10 Homeで、これも初めて使う。

以下やったこと

* Chromeインストール
  - McAfeeプラグイン削除
  - React Developer Toolsインストール
* トラックパッドの設定変更
  - スクロール方向を逆に
  - タップでクリックをオフに
* キーボードの設定変更
  - 表示間隔を最短に
* 画面倍率の設定変更
  - 150%を125%に
* IMEの設定変更
  - IME入力モード切替の通知をオフに
  - 「無変換」キーをIMEオフに割り当て
  - 「変換」キーをIMEオンに割り当て
* Gitインストール
  - CRLFの設定をfalseにした以外はデフォルトで
* VSCodeインストール
* VSCode設定変更
  - Telemetry系をオフに
  - デフォルトのターミナルをgitbashに
  - `workbench.editor.enablePreview`をfalseに
  - Auto Saveを有効に
* node.jsインストール
  - `Tools for Native Modules`のページのチェックをオンに
* yarnインストール
  - PowerShellを管理者権限で起動して、`choco install yarn`
  - chocoコマンドは、node.jsインストール時に入る
* VSCodeプラグイン
  - Debugger for Chrome
* cross-envインストール
  - https://github.com/kentcdodds/cross-env#readme
  - package.jsonで環境変数を設定するときに、OSの違いを吸収してくれる
  - https://qiita.com/riversun/items/d45b26f4a7aad6e51b69
* `NODE_OPTIONS='--inspect'`をつけると、`Starting inspector on 127.0.0.1:9229 failed: address already in use`が出続ける
  - 最新のNext.jsの不具合らしい
  - https://github.com/zeit/next.js/issues/11030
  - `yarn upgrade next@9.2.0`でダウングレードしてみる
    - 表示頻度は下がったが、まだ出る
* spacedeskのインストール
  - モバイルディスプレイ代わりにCT100PA（Chromebookタブレット）を使ってみる
  - HTML5版だとタッチ反応しなかったけれど、Andriodアプリ版だとタッチ反応する
