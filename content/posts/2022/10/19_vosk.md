---
title: "Vosk使ってみる"
date: "2022-10-19"
tags: ["Vosk"]

---

[日本語音声のマイク入力をオフラインでリアルタイム音声認識：「VOSK」を JavaScript（Node.js）で扱う - Qiita](https://qiita.com/youtoy/items/649dcad9ecccf75a9d01)
こちらを参考に。

早速`npm install vosk`したところ、GitbashだとVisualStudioが見つからない的なエラー。WSL2環境で動かしたら通った。

そしてサンプルをコピーして実行すると、エラー。
マイク入力デバイスが見つからないっぽい。WSL環境からは見えないのかも。

GitBashで動かすと、node_modulesがwindows用ではない的なエラー。

[USB デバイスを接続する | Microsoft Learn](https://learn.microsoft.com/ja-jp/windows/wsl/connect-usb)をすればUSBマイク認識してくれるかなぁ。。

> PowerShell を "管理者" モードで開き、次のコマンドを入力することで、Windows に接続されたすべての USB デバイスの一覧を表示します。
```sh
> usbipd wsl list
usbipd : 用語 'usbipd' は、コマンドレット、関数、スクリプト ファイル、または操作可能なプログラムの名前として認識されま
せん。名前が正しく記述されていることを確認し、パスが含まれている場合はそのパスが正しいことを確認してから、再試行してく
ださい。
```
ダメだった。
