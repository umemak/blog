---
title: "nginxで80番ポートの向き先を変更する"
date: "2020-05-25"
tags: ["nginx", "wikijs"]
---

Wiki.jsをservice化したときに、nobodyユーザーだと80番ポートでlistenできないので、Wiki（node.js）はデフォルトの3000番に戻して、nginxでプロキシすることにした。

https://docs.requarks.io/install/linux の`Run as service`をやりたかった。
ホームディレクトリに展開していたwikiを/var/にmvして、sqliteのデータファイルのパスも変更、ファイルのパーミッションをまとめてnobodyに変更。
```
$ cd ~
$ mv wiki /var/
$ sudo chown -R nobody /var/wiki
$ sudo vim /var/wiki/config.yml
```

nginxのインストールと設定
```
$ sudo apt install nginx
$ sudo vim /etc/nginx/conf.d/default.conf
```

default.confの内容
```
server {
        listen 80 default_server;
        server_name _;
        location / {
                proxy_pass http://127.0.0.1:3000;
        }
}
```

nginx再起動
```
$ sudo systemctl restart nginx
```
これで起動しない。`/var/log/nginx/error.log`をみると、以下のエラーが。
```
a duplicate default server for 0.0.0.0:80 in /etc/nginx/sites-enabled/default:22
```
`/etc/nginx/sites-enabled/default`と衝突していると。なので、`/etc/nginx/sites-enabled/default`を削除。`/etc/nginx/sites-available/default`と同じ中身なので、躊躇なく削除して問題ない。

その後nginxを再起動すると、無事wikiが表示された。
