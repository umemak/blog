---
title: "Goのconst"
date: "2022-03-04"
tags: ["go"]

---

EOTとかbyteのスライスをconstで定義しようとしてできなかった。

```
const EOT = []byte{0x00, 0xFF, 0x2F, 0x00}
```

```
$ go run cmd/mdmml/main.go 
# github.com/umemak/mdmml
./mdmml.go:10:7: const initializer []byte{...} is not a constant
```

[The Go Programming Language Specification - The Go Programming Language](https://go.dev/ref/spec#Constants)

文字列リテラルが許されるならbyteスライスも許されてもよいではないかと思ったけれど、ダメらしい。
varで我慢する。
