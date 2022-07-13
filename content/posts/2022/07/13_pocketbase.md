---
title: "PocketBase"
date: "2022-07-13"
tags: ["PocketBase"]

---

supabaseと格闘していたら、[PocketBase - Open Source backend in 1 file](https://pocketbase.io/)という似たような機能を提供するツールを見つけた。

GitHub見ると1週間ほど前に公開されたばかりのよう。

```dockerfile:Dockerfile.pocketbase
FROM alpine

WORKDIR /app

RUN wget https://github.com/pocketbase/pocketbase/releases/download/v0.2.4/pocketbase_0.2.4_linux_amd64.zip
RUN unzip pocketbase_0.2.4_linux_amd64.zip
RUN rm pocketbase_0.2.4_linux_amd64.zip

CMD [ "/app/pocketbase", "serve", "--http", "0.0.0.0:8090" ]
```
これで`http://0.0.0.0:8090/_/`にアクセスしたら管理者アカウントの作成画面が出た。
`--http`オプション指定しないとアクセスできない。

```yml:docker-compose.yml
version: '3'

services:
  pocketbase:
    image: pocketbase:local
    build:
      context: .
      dockerfile: Dockerfile.pocketbase
    volumes:
      - ./pb_data:/app/pb_data
    ports:
      - 8090:8090
```
これでコンテナ落としてもデータは保持される。

ユーザー作ってみる
```sh
$ curl -v -X POST -H 'Content-Type: application/json' --data '{"email": "email@example.com", "password": "secret123", "passwordConfirm": "secret123"}' 'http://localhost:8090/api/users'|jq .
{
  "id": "EnFokKc3NvP1f88",
  "created": "2022-07-13 10:08:35.276",
  "updated": "2022-07-13 10:08:35.276",
  "email": "email@example.com",
  "lastResetSentAt": "",
  "verified": false,
  "lastVerificationSentAt": "",
  "profile": {
    "@collectionId": "hchwXTv3ajveMt7",
    "@collectionName": "profiles",
    "created": "2022-07-13 10:08:35.276",
    "id": "OPV0nDugyANdoIV",
    "updated": "2022-07-13 10:08:35.276",
    "userId": "EnFokKc3NvP1f88"
  }
}
```
いけるやん。
