+++
author = "umemak"
date = "2019-08-04"
title = "ghqのインストール"
tags = ["go"]
archives = "2019/08"
+++

* 「改訂2版 みんなのGo言語」を買ったのでC101PAで試しながら読みすすめていた。
* ghqをインストールするところでエラー。
* どうやらgoのバージョンを1.12以上にあげないとダメらしい。
* 先日パッケージでインストールしたgoは1.11.6だった。
* [以前のやり方](https://github.com/umemak/blog/blob/master/2019/07/17_chromebook_golang.md)でインストールし直す
* ~/.bash_profile の `GOROOT` は `/usr/local/go` に変更してsourceする。
* 無事インストール完了。
