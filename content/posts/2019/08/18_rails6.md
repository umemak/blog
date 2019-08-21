---
author: "umemak"
date: 2019-08-18
title: Rails6を試す
# tags: [ "rails" ]
---

* リリースされていたので、アップデートしてみる
  https://weblog.rubyonrails.org/2019/8/15/Rails-6-0-final-release/
* 対象
  https://github.com/umemak/hello_app
* Gemfileを編集
  ```
  gem 'rails', '>=6.0.0'
  ```
* bundle updateする環境を準備
  ```
  docker run -it -v `pwd`:/usr/src/work ruby bash
  ```
* bundle update
  ```
  root@5655bc438c4d:/usr/src/work# bundle update
  Fetching gem metadata from https://rubygems.org/............
  Fetching gem metadata from https://rubygems.org/.
  Resolving dependencies....
  Bundler could not find compatible versions for gem "railties":
    In Gemfile:
      coffee-rails (= 4.2.2) was resolved to 4.2.2, which depends on
        railties (>= 4.0.0)

      jquery-rails (= 4.3.1) was resolved to 4.3.1, which depends on
        railties (>= 4.2.0)

      rails (>= 6.0.0) was resolved to 6.0.0, which depends on
        railties (= 6.0.0)

      sass-rails (= 5.0.6) was resolved to 5.0.6, which depends on
        railties (>= 4.0.0, < 6)

      web-console (= 3.5.1) was resolved to 3.5.1, which depends on
        railties (>= 5.0)

  Bundler could not find compatible versions for gem "spring":
    In Gemfile:
      spring (= 2.0.2)

      spring-watcher-listen (= 2.0.1) was resolved to 2.0.1, which depends on
        spring (>= 1.2, < 3.0)
  ```
  とりあえず、エラーになっているgemのバージョン指定に`>=`をつけてupdateできた。
  ```
  root@5655bc438c4d:/usr/src/work# rails -v
  Rails 6.0.0
  ```
* 動作確認
  ```
  rails s
  ```
  execjsでエラー。https://github.com/rails/execjs の通りにgemをインストール
  ```
  gem install execjs
  ```
  まだエラー。JSの実行環境も必要らしいのでnodejsをインストール
  ```
  apt update
  apt install nodejs -y
  ```
  ```
  root@d02c06050dc6:/usr/src/work# rails s
  => Booting Puma
  => Rails 6.0.0 application starting in development 
  => Run `rails server --help` for more startup options
  Puma starting in single mode...
  * Version 3.9.1 (ruby 2.6.3-p62), codename: Private Caller
  * Min threads: 5, max threads: 5
  * Environment: development
  * Listening on tcp://0.0.0.0:3000
  Use Ctrl-C to stop
  ```
  動いた！
  が、port開け忘れた。。。
  docker再起動してもいいけどbundle install時間かかるし。。
* docker commit
  別のターミナル開いて、イメージにタグつけて保存して起動しなおす
  ```
  $ docker commit 5655bc438c4d rails6test
  $ docker run -it -p 3000:3000 -v `pwd`:/usr/src/work rails6test bash
  root@d02c06050dc6:/usr/src/work# rails s
  => Booting Puma
  => Rails 6.0.0 application starting in development 
  => Run `rails server --help` for more startup options
  Puma starting in single mode...
  * Version 3.9.1 (ruby 2.6.3-p62), codename: Private Caller
  * Min threads: 5, max threads: 5
  * Environment: development
  * Listening on tcp://0.0.0.0:3000
  Use Ctrl-C to stop
  ```
  できた。
* http://127.0.0.1:3000
  ```
  2019-08-18 02:08:23 +0000: Rack app error handling request { GET / }
  #<LoadError: Error loading the 'sqlite3' Active Record adapter. Missing a gem it depends on? can't activate sqlite3 (~> 1.4), already activated sqlite3-1.3.13. Make sure all dependencies are added to Gemfile.>
  ```
  む。。。
  Gemfileのsqlite3もバージョン指定を緩める。
  ```
  Started GET "/" for 172.17.0.1 at 2019-08-18 02:19:05 +0000
  Cannot render console from 172.17.0.1! Allowed networks: 127.0.0.0/127.255.255.255, ::1
     (5.8ms)  SELECT sqlite_version(*)
  Processing by ApplicationController#hello as HTML
    Rendering html template
    Rendered html template (Duration: 1.9ms | Allocations: 5)
  Completed 200 OK in 39ms (Views: 30.3ms | ActiveRecord: 0.0ms | Allocations: 1383)
  ```
  できた！
* https://github.com/umemak/hello_app/commit/84cc280f3776cc72d85c9bac088f8ef50cd5eaf8
