---
title: "OpenAPIで生成したサーバーのテスト2"
date: "2022-09-18"
tags: ["TypeScript", "OpenAPI"]

---

E2Eテスト書くなら、OpenAPIのクライアントコードジェネレータ使って出力したもの使えばよいのでは？
と思いついたので、どのクライアントにしようかと[Generators List](https://openapi-generator.tech/docs/generators#client-generators)を眺める。

せっかくだからTypeScriptが良いなと思うが、11種類もあってどれが適切なのか判断付かない。
実際に生成して使って比較すればよいのだろうけど、そこまで詳しくない言語でそれをやろうとすると挫折する気しかしない。

一覧に載っているもの以外にもある
- [ferdikoomen/openapi-typescript-codegen: NodeJS library that generates Typescript or Javascript clients based on the OpenAPI specification](https://github.com/ferdikoomen/openapi-typescript-codegen)
- [Himenon/openapi-typescript-code-generator: TypeScript code generator via OpenAPI scheme.](https://github.com/Himenon/openapi-typescript-code-generator)

やっぱりGoで書くのが手っ取り早いかな。。
