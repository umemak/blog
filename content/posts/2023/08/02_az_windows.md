---
title: "Windowsにazコマンドのインストール"
date: "2023-08-02"
tags: ["Azure"]

---

[Azure CLI をインストールする方法 | Microsoft Learn](https://learn.microsoft.com/ja-jp/cli/azure/install-azure-cli)からインストーラーをダウンロードしてインストールしたら、32bit版で実行するたびにメッセージが出て気になったので、アンインストールして別の方法を探った。

[Support Azure CLI 64-bit on Windows · Issue #18766 · Azure/azure-cli](https://github.com/Azure/azure-cli/issues/18766)でpip使ってインストールしたら回避できると書かれていたのでやってみたら、インストールに失敗する。
エラーメッセージを見ると

> HINT: This error might have occurred since this system does not have Windows Long Path support enabled. You can find information on how to enable this at https://pip.pypa.io/warnings/enable-long-paths

とのことなので、レジストリエディタで変更したらエラーは解消した。

が、`az`実行しても`command not found`で動かず。

こういう環境周りで苦労するのつらい。

→結局docker使った。
