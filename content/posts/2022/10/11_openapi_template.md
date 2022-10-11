---
title: "OpenAPI generatorのテンプレート"
date: "2022-10-11"
tags: ["OpenAPI"]

---

以前、OpenAPI generatorの出力をカスタマイズするにはJavaを読み解かねば・・みたいなことを書いていた。

- [OpenAPIとsqlcの連携 - umemak](https://umemak.github.io/blog/posts/2022/08/04_openapi_sqlc/)
- [OpenAPI generatorのソース - umemak](https://umemak.github.io/blog/posts/2022/08/05_openapi_generator_src/)

[テンプレートの使用](https://openapi-generator.tech/docs/templating/)によると、`author template`を指定すれば組み込みテンプレートが出力されるとのこと。で、出力されたディレクトリを`-t`で指定すると、そこにあるテンプレートを使って生成される。

つまり、
```sh
MSYS_NO_PATHCONV=1 docker run --rm \
  -v ${PWD}:/local openapitools/openapi-generator-cli author template \
  -g go-server \
  -o /local/template
```
でカレントディレクトリの`template`にmustache形式のテンプレートファイルが作成されるので、好きなように編集して、
```sh
MSYS_NO_PATHCONV=1 docker run --rm \
  -v ${PWD}:/local openapitools/openapi-generator-cli generate \
  -t /local/template \
  -i /local/openapi.yml \
  -g go-server \
  --additional-properties=router=chi,featureCORS=true \
  -o /local/out
```
こうするとカスタマイズした出力が得られる。

ドキュメントはちゃんと読みましょう。
