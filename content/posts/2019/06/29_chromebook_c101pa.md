---
author: "umemak"
date: 2019-06-29
title: C101PA届いた
# tags: [ "C101PA", "chromebook" ]
---

* 起動直後はOSが古い→ChromeOSバージョンアップ実施
* Googleアンケートアプリが対応していない
  - C223NAも再インストールしたらインストールできなくなっていた。。
* Kindleアプリインストールできた
* 全体的にC223NAに比べて遅い（知ってた）
* 今回は開発者モードにしないで普通にLinux有効化した
* brewインストール
  ```
  $ sh -c "$(curl -fsSL https://raw.githubusercontent.com/Linuxbrew/install/master/install.sh)"
  $ test -d ~/.linuxbrew && PATH="$HOME/.linuxbrew/bin:$HOME/.linuxbrew/sbin:$PATH"
  $ test -d /home/linuxbrew/.linuxbrew && PATH="/home/linuxbrew/.linuxbrew/bin:/home/linuxbrew/.linuxbrew/sbin:$PATH"
  $ test -r ~/.bash_profile && echo "export PATH='$(brew --prefix)/bin:$(brew --prefix)/sbin'":'"$PATH"' >>~/.bash_profile
  $ echo "export PATH='$(brew --prefix)/bin:$(brew --prefix)/sbin'":'"$PATH"' >>~/.profile
  $ Homebrew 2.1.6
  Homebrew/linuxbrew-core (git revision bb5a; last commit 2019-06-29)
  ```
* golangインストール
  ```
  $ wget https://dl.google.com/go/go1.12.6.linux-amd64.tar.gz
  $ tar zxvf go1.12.6.linux-amd64.tar.gz
  $ sudo mv go /usr/local/go1.12.6
  $ sudo ln -s /usr/local/go1.12.6 /usr/local/go
  $ /usr/local/go/bin/go version
  -bash: /usr/local/go/bin/go: cannot execute binary file: Exec format error
  ```
  だめか。。

* golangインストール（apt）
  ```
  $ sudo apt-get update
  $ sudo apt-get install golang
  $ go version
  go version go1.7.4 linux/arm64
  ```
  きた・・！でもちょっと古い？

* rubyもインストール
  ```
  $ sudo apt-get install ruby
  $ ruby -v
  ruby 2.3.3p222 (2016-11-21) [aarch64-linux-gnu]
  ```
  これも最新ではないけれどまあ仕方ない

* VSCode
  ```
  $ sudo apt-get install snapd
  $ sudo snap install --classic code
  error: cannot install "code": snap not found
  ```
  うーん。。
