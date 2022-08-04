---
title: "OpenAPIとsqlcの連携"
date: "2022-08-04"
tags: ["OpenAPI", "sqlc"]

---

[Documentation for the go-server Generator](https://openapi-generator.tech/docs/generators/go-server/)で生成したファイルと[sqlc.dev | Compile SQL to type-safe Go](https://sqlc.dev/)で生成したファイル、うまく連携できればもっと手数少なくAPIサーバーが作れるのになー・・

現状用意するものとしては、DDLとqueryとAPI定義で、APIのリソースとDBのテーブルが1:1なら決め打ちでかける部分が出てくるはず・・

どちらに寄せるかは、OpenAPI定義側かなぁ。。
OpenAPI定義からDDLが生成できれば、queryはサーバーコードと一緒でも良いと思うし。
