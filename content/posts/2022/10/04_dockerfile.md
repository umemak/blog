---
title: "Dockerfileでブレース展開"
date: "2022-10-04"
tags: ["docker"]

---

golangのベースイメージにnodejsを入れたくて、
[Step by step instructions to install node and npm using Linux binaries - DEV Community 👩‍💻👨‍💻](https://dev.to/aashishpanthi/step-by-step-instructions-to-install-node-and-npm-using-linux-binaries-1e0h)
この手順見ながらやってみていたのだけれど、

```Dockerfile
RUN cp -r ./{lib,share,include,bin} /usr
```

でファイル未存在のエラーになってしまった。

```Dockerfile
RUN cp -r ./lib /usr
RUN cp -r ./share /usr
RUN cp -r ./include /usr
RUN cp -r ./bin /usr
```

とすると通るので、ファイルが存在しないわけではなく、ブレース展開ができていないらしい。

少し調べてみたけれど、解決方法わからず。

ベースイメージをnodeにしてgoを後からインストールしたほうが簡単な気がしてきた。
