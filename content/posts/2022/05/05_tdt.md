---
title: "TypeScriptでTable Driven Test"
date: "2022-05-05"
tags: ["TypeScript", "test"]

---

もともとGoで書いていたテストが[こんな感じ](https://github.com/umemak/mdmml/blob/main/mdmml_test.go#L162-L190)だったのだけど、
[こんな風に](https://github.com/umemak/mdmml_js/blob/7930f4f23801ac0a58c645284c5d2091d8fa8024/src/mdmml.test.ts#L22-L56)移植してて面倒だと感じていた。

[TS と Jest で Table Driven Test をする · tblog](https://tblog.acomagu.me/plh/)を参考に書き換えて、[こうなった](https://github.com/umemak/mdmml_js/blob/716849f09419651500e25750d6e0b43514f04e6b/src/mdmml.test.ts#L31-L48)。

