---
title: "loofahアップデート"
date: "2018-11-03"
tags: ["ruby"]
---

* GitHubからメールきた
  ```
  Known moderate severity security vulnerability detected in loofah < 2.2.3 defined in Gemfile.lock.
  Gemfile.lock update suggested: loofah ~> 2.2.3.
  ```

* 作ったときのCloud9環境は削除してしまったので、Macローカルで更新する。
  - 対象リポジトリをclone。
    ```
    $ git clone https://github.com/umemak/sample_app.git
    ```
  - bundle installで更新
    ```
    $ bundle install
    
    Fetching gem metadata from https://rubygems.org/.........
    
    activesupport-5.1.6 requires ruby version >= 2.2.2, which is incompatible with the current version, ruby2.1.9p490
    ```
    できない
  - dockerで
    ```
    $ docker run -it -v `pwd`:/home/k ruby bash
    
    root@bf0de34089b9:/# cd /home/k
    
    root@bf0de34089b9:/home/k# bundle install
    
    Fetching gem metadata from https://rubygems.org/.........
    
    （中略）
    
    Bundle complete! 21 Gemfile dependencies, 82 gems now installed.
    
    Bundled gems are installed into `/usr/local/bundle`
    
    root@bf0de34089b9:/home/k# grep loofah Gemfile.lock
    
        loofah (2.2.2)
    
          loofah (~> 2.2, >= 2.2.2)
    ```
    あがってない
  - updateじゃないとだめらしい
    ```
    root@bf0de34089b9:/home/k# bundle update
    
    Fetching gem metadata from https://rubygems.org/.........
    
    Fetching gem metadata from https://rubygems.org/.
    
    Resolving dependencies...
    
    Using rake 12.3.1
    
    （中略）
    
    Using web-console 3.5.1
    
    Bundle updated!
    ```
  - 確認
    ```
    root@bf0de34089b9:/home/k# grep loofah Gemfile.lock
    
        loofah (2.2.3)
    
          loofah (~> 2.2, >= 2.2.2)
    ```
    OK。
  - DockerからexitしてGitHub更新。
    ```
    $ git commit -am "update loofah"
    
    [master 4d2d9c3] update loofah
    
    2 files changed, 6 insertions(+), 3 deletions(-)
    
    $ git push origin HEAD
    
    Counting objects: 4, done.
    
    Delta compression using up to 8 threads.
    
    Compressing objects: 100% (4/4), done.
    
    Writing objects: 100% (4/4), 423 bytes | 423.00 KiB/s, done.
    
    Total 4 (delta 3), reused 0 (delta 0)
    
    remote: Resolving deltas: 100% (3/3), completed with 3 local objects.
    
    To https://github.com/umemak/sample_app.git
    
       61a32a4..4d2d9c3  HEAD -> master
    ```
