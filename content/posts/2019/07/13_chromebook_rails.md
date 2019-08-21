---
author: "umemak"
date: 2019-07-13
title: chromebookにrailsをインストール
---

# chromebookにrailsインストール

## 狙い
* たまにあるgemの脆弱性対応、cloud9使わずにできるようにならないか？

## 環境
* C223NAのLinux(beta)

## 実践
* ruby と関連パッケージインストール
  ```
  $ sudo apt-get install ruby ruy-dev zlib1g-dev build-essential patch postgresql libpq-dev libsqlite3-dev nodejs
  ```
  - `ruby`以外のパッケージは`bundle install`や`rails s`時に必要。
  - 参考：https://technotes.tt4living.com/ruby-on-rails/install-ruby-on-rails
  - `postgresql`は無くても良いかも。

* rails と bundler インストール
  ```
  $ sudo gem install rails bundler
  ```

* ソース取得してbundle install
  ```
  $ mkdir ~/workspace
  $ cd ~/workspace
  $ git clone https://github.com/umemak/hello_app.git
  $ cd hello_app
  $ bundle install --path=vendor/bundle
  $ rails s
  ```

## まとめ
* 当初の目的は達成できそう
* bundle installはそれなりに時間がかかる
* 関連パッケージ多いので容量が心配
