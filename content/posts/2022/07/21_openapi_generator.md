---
title: "OpenAPI Generator"
date: "2022-07-21"
tags: ["OpenAPI"]

---

[Generators List](https://openapi-generator.tech/docs/generators#schema-generators)を眺めていたら、[mysql-schema](https://openapi-generator.tech/docs/generators/mysql-schema)なんてのがあったので、試してみた。

```sh
$ wget https://raw.githubusercontent.com/openapitools/openapi-generator/master/modules/openapi-generator/src/test/resources/3_0/petstore.yaml
$ docker run --rm \
  -v ${PWD}:/local openapitools/openapi-generator-cli generate \
  -i /local/petstore.yaml \
  -g mysql-schema \
  -o /local/out
$ ls -R out/
out/:
Model  README.md  mysql_schema.sql

out/Model:
ApiResponse.sql  Category.sql  Order.sql  Pet.sql  Tag.sql  User.sql
```

`out/mysql_schema.sql`にDDLが作成されていた。

`out/Model`には、CRUD用SQLのテンプレートが作られていた。

`petstore.yaml`の`components > schemas`の定義がもとになっているのかな。

制約とか表現できてないので、出力されたものをそのまま使うことはできないけれど、可能性を感じられるツールだと思う。
