---
title: "OpenAPIのyamlを結合する"
date: "2023-09-29"
tags: ["OpenAPI"]

---

一つのopenapi.yamlに定義を書いていると、ファイルが肥大化して管理というか編集が大変になる。

で、分割するには`$ref`を使って相対ファイル指定することで、外部ファイルを参照できる。

ただ、Swagger UIでダウンロードしようとすると、ルートのファイルしか取れない（相対ファイルを辿ればとれるだろうけど面倒）。

そこで分割したファイルを結合するのに[@apidevtools/swagger-cli - npm](https://www.npmjs.com/package/@apidevtools/swagger-cli)を使おうとしたところ、deprecatedとのこと。

代わりに使ったのが[@redocly/cli - npm](https://www.npmjs.com/package/@redocly/cli)。

結合するだけなら特に問題なさそうだし、lintも付いていて良い。
