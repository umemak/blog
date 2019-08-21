---
author: "umemak"
date: 2019-08-21
title: Hugoの導入
---

# Hugoの導入
* やってみよう

## インストール
https://gohugo.io/getting-started/installing/#linux を見たら apt でいけるらしいので
```
$ apt install hugo
$ hugo version
Hugo Static Site Generator v0.18.1 BuildDate: 2016-12-31T01:01:10+09:00
```
v0.18.1 ってだいぶ古い。。
```
$ sudo apt remove hugo
$ wget https://github.com/gohugoio/hugo/releases/download/v0.57.2/hugo_extended_0.57.2_Linux-64bit.tar.gz
$ sha256sum hugo_extended_0.57.2_Linux-64bit.tar.gz 
f4ce91d6909d489fe5461633f6b6bd689ed14c9e06b1b7af110024420aa8fd91  hugo_extended_0.57.2_Linux-64bit.tar.gz
$ tar zxvf hugo_extended_0.57.2_Linux-64bit.tar.gz 
LICENSE
README.md
hugo
$ sudo cp hugo /usr/local/bin/
$ hugo version
Hugo Static Site Generator v0.57.2-A849CB2D/extended linux/amd64 BuildDate: 2019-08-17T17:57:54Z
```
OK。

## サイト作成
```
$ hugo new site blog
```

## テーマ追加
```
$ cd blog
$ git clone https://github.com/Track3/hermit.git themes/hermit
$ echo 'theme = "hermit"' >> config.toml
```

## コンテンツ追加
```
$ hugo new posts/my-first-post.md
```

## 表示確認
```
$ hugo server -D
Building sites … ERROR 2019/08/21 11:29:11 render of "section" failed: execute of template failed: template: _default/list.html:21:50: executing "main" at <.Site.Params.dateformshort>: invalid value; expected string
ERROR 2019/08/21 11:29:11 render of "taxonomyTerm" failed: execute of template failed: template: _default/list.html:21:50: executing "main" at <.Site.Params.dateformshort>: invalid value; expected string
ERROR 2019/08/21 11:29:11 render of "taxonomy" failed: execute of template failed: template: _default/list.html:21:50: executing "main" at <.Site.Params.dateformshort>: invalid value; expected string
Total in 167 ms
Error: Error building site: failed to render pages: render of "page" failed: "/home/umemak/blog/themes/hermit/layouts/posts/single.html:22:54": execute of template failed: template: posts/single.html:22:54: executing "main" at <.Site.Params.dateform>: invalid value; expected string
```
なんかエラーでた。。
`hermit/exampleSite/config.toml`を`config.toml`にコピーして解消。
`[params]`セクションがないとだめらしい。

## 必要なファイルのコピー
こっちのリポジトリに反映する
```
$ cd
$ git clone https://github.com/umemak/umemak.github.io.git
$ cp -r ./blog/{archetypes,data,layouts,themes,config.toml} ./umemak.github.io.git/
$ cd umemak.github.io.git
$ mkdir -p content/posts
$ mv blog content/posts
```

## 設定の変更
config.tomlを修正
https://github.com/umemak/umemak.github.io/blob/master/config.toml

## 生成＆push
```
$ hugo
$ git add .
$ git commit -am "hugo"
$ git push origin HEAD
```

## 確認
https://umemak.github.io/blog/

## まとめ
* 手動で更新するところかでできた。次はCI対応。
* Github Pages って master に docs があればそこがルートになるっぽいのに、なってくれない。
  - 一度作り直さないとだめ？
* テーマ選びに意外と時間がかかった。。
