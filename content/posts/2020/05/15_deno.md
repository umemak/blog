---
title: "DenoをChromebookで使ってみる"
date: "2020-05-15"
tags: ["deno"]
---

Denoのバージョン1が出たというニュース記事を見て、試してみた。

https://deno.land/v1

Node.jsを作者自ら作り直したもの。

最初にRasperry Pi 4で試したところ、公式のインストーラーが`x86_64`しか対応していなかったので断念。
[ソースからビルドする手順](https://deno.land/manual/contributing/building_from_source)も試してみたけれど、途中でエラーになってしまう。

armで動くようになればきっと裾野が広がるだろうなと思いつつ、ひとまず使ってみたかったのでChromebook C223NAで実行。

ChromebookのLinuxで公式のインストール手順使って何も問題なくインストールできた。
```
$ deno --version
deno 1.0.0
v8 8.4.300
typescript 3.9.2
$ deno run https://deno.land/std/examples/welcome.ts
Download https://deno.land/std/examples/welcome.ts
Warning Implicitly using master branch https://deno.land/std/examples/welcome.ts
Compile https://deno.land/std/examples/welcome.ts
Welcome to Deno 🦕
$ deno run https://deno.land/std/examples/welcome.ts
Welcome to Deno 🦕
```
初回実行はダウンロードとコンパイルが走っているが、２回目は即実行されるので速い。
