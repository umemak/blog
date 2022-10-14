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
