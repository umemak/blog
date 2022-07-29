---
title: "OpenAPI Generator go-server"
date: "2022-07-29"
tags: ["OpenAPI"]

---

[Documentation for the go-server Generator](https://openapi-generator.tech/docs/generators/go-server/)で、routerは`mux`と`chi`が選べると書いてあって、省略時は`mux`とのこと。

`chi`の指定方法がわからなかったので調べた。

```sh
$ wget https://raw.githubusercontent.com/openapitools/openapi-generator/master/modules/openapi-generator/src/test/resources/3_0/petstore.yaml
$ docker run --rm \
  -v ${PWD}:/local openapitools/openapi-generator-cli generate \
  -i /local/petstore.yaml \
  -g go-server \
  --additional-properties=router=chi \
  -o /local/out
```

と、`--additional-properties`につけるらしい。、
他のパラメータ、たとえば`sererPort`も指定したい場合はカンマ区切りで`--additional-properties=router=chi,sererPort=18080`こう。

ちゃんとドキュメントに書かれているけど、あまり見ない書き方なので備忘録として。

- [Usage](https://openapi-generator.tech/docs/usage/#additional-properties)
