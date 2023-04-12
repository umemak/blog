---
title: "Drupal"
date: "2023-04-12"
tags: []

---

記事で久しぶりに名前を見て、dockerイメージが用意されていたので動かしてみた。

[drupal - Official Image | Docker Hub](https://hub.docker.com/_/drupal)

上記ページのdocker-compose.ymlをコピペで試したら、バージョンが古かったので最新の10系で起動。

起動したけどセットアップ時にPostgreSQLへの接続がうまくいかず、MySQLに変更したらいけた。

```yaml
# Drupal with PostgreSQL
#
# Access via "http://localhost:8080"
#   (or "http://$(docker-machine ip):8080" if using docker-machine)
#
# During initial Drupal setup,
# Database type: PostgreSQL
# Database name: postgres
# Database username: postgres
# Database password: example
# ADVANCED OPTIONS; Database host: postgres

version: '3.1'

services:

  drupal:
    image: drupal:10-apache
    ports:
      - 8080:80
    volumes:
      - /var/www/html/modules
      - /var/www/html/profiles
      - /var/www/html/themes
      # this takes advantage of the feature in Docker that a new anonymous
      # volume (which is what we're creating here) will be initialized with the
      # existing content of the image at the same location
      - /var/www/html/sites
    restart: always

  # postgres:
  #   image: postgres:15
  #   environment:
  #     POSTGRES_PASSWORD: example
  #   restart: always

  mysql:
    image: mysql:8
    command: --default-authentication-plugin=mysql_native_password
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: example
```
