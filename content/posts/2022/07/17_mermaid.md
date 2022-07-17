---
title: "mermaidのER図"
date: "2022-07-17"
tags: ["mermaid"]

---

VS Codeのmermaid拡張でER図を試していて、カラム名に日本語使えなくて論理名と物理名両方書きたいのにどうしようかと思ったら、コメントとして書けば日本語も通ることに気づいた。

[mermaid - Markdownish syntax for generating flowcharts, sequence diagrams, class diagrams, gantt charts and git graphs.](https://mermaid-js.github.io/mermaid/#/./entityRelationshipDiagram?id=attribute-keys-and-comments)

つまり、こう書ける。
```mermaid
erDiagram

user {
  bigint id PK "ID Auto increment"
  text email  "メール"
  text name  "名前"
}
```

型とカラム名はどっちが先でも通るっぽい。
```mermaid
erDiagram

user {
  id bigint PK "ID Auto increment"
  email text  "メール"
  name text  "名前"
}
```
こっちのほうがDDLに近いから良い気がするんだけど、どうだろう。
