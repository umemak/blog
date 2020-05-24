---
title: "Wiki.jsを試す"
date: "2020-05-24"
tags: ["wikijs"]
---

GCP無料枠でWikiを動かしてみるシリーズ。
今回はWiki.js。

docker-composeを使う方法も用意されているが、軽量優先で通常インストールのほうで。

https://docs.requarks.io/install/linux

`config.yml`の編集では、ポートを80に、DBをsqliteに変更した。

```
$ sudo apt install wget nodejs npm
$ wget https://github.com/Requarks/wiki/releases/download/2.3.81/wiki-js.tar.gz
$ mkdir wiki
$ tar xzf wiki-js.tar.gz -C ./wiki
$ cd ./wiki
$ mv config.sample.yml config.yml
$ nano config.yml
$ npm rebuild sqlite3
$ sudo node server
```

動いた・・・！
