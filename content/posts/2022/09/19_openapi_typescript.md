---
title: "OpenAPIのTypeScriptクライアント"
date: "2022-09-19"
tags: ["TypeScript", "OpenAPI"]

---

結局、いくつか動かして試してみた。`additional-properties`は無指定で。

- [Documentation for the typescript-fetch Generator](https://openapi-generator.tech/docs/generators/typescript-fetch)
  - `ReferenceError: _ is not defined`
- [Documentation for the typescript-node Generator](https://openapi-generator.tech/docs/generators/typescript-node)
  - `Module not found: Can't resolve 'request'`
  - requestパッケージは[Deprecated!](https://github.com/request/request#deprecated)らしい。
- [Documentation for the typescript-axios Generator](https://openapi-generator.tech/docs/generators/typescript-axios)
  - とりあえず動いた。
  - axiosパッケージの追加インストールが必要。

ということで、typescript-axios でやってみようと思う。
