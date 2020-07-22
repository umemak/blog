---
title: "Raspberry pi4 で expo を動かす"
date: "2020-07-22"
tags: ["expo", "raspberry_pi"]
---

WSLでいろいろ試してみたものの、ポート関連のエラーで動かないので、Raspberry piで試してみた。

## Rubyインストール
Homebrewインストールしようとしたときに、Rubyがないエラーで先に進まなくなってしまったので先にインストールしておく。
`rbenv`を使ってみる。
途中でパッケージが足りないエラーが出るので、`libssl-dev`と`libreadline-dev`を入れる。
```
$ sudo apt-get install -y libssl-dev libreadline-dev
$ git clone https://github.com/rbenv/rbenv.git ~/.rbenv
$ echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
$ echo 'eval "$(rbenv init -)"' >> ~/.bashrc
$ git clone https://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build
$ rbenv rehash
$ rbenv install --list
$ rbenv install 2.6.6
$ rbenv global 2.6.6
$ rbenv rehash
$ ruby --version
ruby 2.6.6p146 (2020-03-31 revision 67876) [aarch64-linux]
```

## Homebrewインストール
Nodejsのバージョン管理したかったので。
手順は先日[WSLにインストール](./20_wsl_brew)したときと同様。
```
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
$ sudo apt-get install build-essential
$ echo 'eval $(/home/linuxbrew/.linuxbrew/bin/brew shellenv)' >> /home/pi/.profile
$ eval $(/home/linuxbrew/.linuxbrew/bin/brew shellenv)
$ brew --version
Homebrew 2.4.8
Homebrew/linuxbrew-core (git revision 39fddf7; last commit 2020-07-21)
```

## Nodebrewインストール
これも先日と同様。
```
$ brew install nodebrew
$ mkdir -p ~/.nodebrew/src
$ nodebrew install stable
$ nodebrew ls
$ nodebrew use v14.6.0
$ vi ~/.profile
export PATH=$HOME/.nodebrew/current/bin:$PATH
$ source ~/.profile
$ node -v
v14.6.0
```

## Expoインストール
グローバルに`expo-cli`をインストールしないで、init後にaddしている。
テンプレートは`tabs (TypeScript)`を選択した。
```
$ cd workspace/
$ npx expo-cli init expotest
$ cd expotest/
$ npm install --save-dev expo-cli
```
`npm start`後、しばらくすると以下のエラーが出るので、上限を上げる。
```
Error: ENOSPC: System limit for number of file watchers reached, watch '/home/pi/workspace/expotest/node_modules/metro/node_modules/string-width/node_modules/ansi-regex'
```
```
$ cat /proc/sys/fs/inotify/max_user_watches
8192
$ sudo su
# echo fs.inotify.max_user_watches= 65536 | tee -a /etc/sysctl.conf
fs.inotify.max_user_watches= 65536
# cat /proc/sys/fs/inotify/max_user_watches
8192
# sysctl -p
fs.inotify.max_user_watches = 65536
# cat /proc/sys/fs/inotify/max_user_watches
65536
# exit
```

## Expo起動
```
$ npm start
```
表示されたQRコードを、iOSやAndroidのアプリで開くと表示される。
初回はJavaScriptのビルドが走る（アプリの画面下部に進捗が表示される）。
それ以降はソースを変更するとほぼリアルタイムで反映される。
