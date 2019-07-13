# chromebookにrailsインストール

## 狙い
* たまにあるgemの脆弱性対応、cloud9使わずにできるようにならないか？

## 環境
* C223NAのLinux(beta)

## 実践
* ruby インストール
  ```
  $ sudo apt-get install ruby ruy-dev zlib1g-dev build-essential patch postgresql libpq-dev libsqlite3-dev
  ```
  - `ruby`以外のパッケージは`bundle install`時に必要。
  - 参考：https://technotes.tt4living.com/ruby-on-rails/install-ruby-on-rails
  - `postgresql`は無くても良いかも。

* ソース取得してbundle install
  ```
  $ mkdir ~/workspace
  $ cd ~/workspace
  $ git clone https://github.com/umemak/hello_app.git
  $ cd hello_app
  $ sudo gem install bundler
  $ bundle install --path=vendor/bundle
  ```

## まとめ
* 当初の目標は達成できそう
* bundle installはそれなりに時間がかかる
