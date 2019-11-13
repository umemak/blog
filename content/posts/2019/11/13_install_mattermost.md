---
title: "Mattermostを使ってみる"
date: "2019-11-13"
tags: ["mattermost"]
---

OracleCloudで動かしてみる。

dockerとdocker-composeとgitをインストール。

https://github.com/mattermost/mattermost-docker をgit cloneして、docker-compose.ymlのパスワードをランダムな文字列に変更したあと、`docker-compose up -d`

```
  Running setup.py install for gevent: started
    Running setup.py install for gevent: still running...
```
が結構時間かかる。

いきなり`docker-compose up -d`ではなく、`docker-compose build`からやったほうが安心かも。

`docker-compose ps`で見ると、`Restarting`ステータスが。`docker-compose logs`で確認。
```
app_1  | cp: can't create '/mattermost/config/config.json': Permission denied
app_1  | /entrypoint.sh: line 36: can't create /mattermost/config/config.json.tmp: Permission denied
```
手順確認すると、ディレクトリ掘って権限設定するのを見落としていた。
```
$ mkdir -p ./volumes/app/mattermost/{data,logs,config,plugins}
$ sudo chown -R 1000:1000 ./volumes/app/mattermost/
```
現象変わらず。。
