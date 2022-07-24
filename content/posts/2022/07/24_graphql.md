---
title: "GraphQL"
date: "2022-07-24"
tags: ["GraphQL"]

---

API設計するのに、GraphQLの可能性はどうなのかと思ってちょっとググってみた。

個人的にはAmplifyを試していたときに良くわからなくて挫折した思い出がある。

なんとなく、参照系はGraphQLで柔軟性を持たせつつ、更新系は従来のリソース志向のAPIで使い分けるのはどうかなと思った。

Goでのサーバー実装は、[99designs/gqlgen: go generate based graphql server library](https://github.com/99designs/gqlgen)がよく使われている感じ。
