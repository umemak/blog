---
title: "WSLのmakeでmkdir"
date: "2022-10-14"
tags: ["WSL"]

---

```Makefile
.PHONY: mkdir
mkdir:
	mkdir -p ./work/{a,b,c}
```
```sh
$ make mkdir 
mkdir -p ./work/{a,b,c}
```
```sh
$ ls work
{a,b,c}
```
なんでや。
```sh
$ rm -r work
```
```sh
$ mkdir -p ./work/{a,b,c}
$ ls work
a  b  c
```
こうなってほしい。


→make内では、デフォルトのシェルが`/bin/sh`になっているので、Makefileで`SHELL=/bin/bash`を書く必要がある。

- [とあるエンジニアの備忘log: Make のポータビリティについて考える](http://masahir0y.blogspot.com/2012/07/make_26.html)
- [Makefileには使用するshellを定義すると良さそう - Qiita](https://qiita.com/nassy20/items/3183cc17f36a3f21e333)
