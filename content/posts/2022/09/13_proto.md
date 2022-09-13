---
title: "proto"
date: "2022-09-13"
tags: ["go", "gRPC"]

---

proto定義何もわからない。。

REST用のパスを定義するために
```
    option (google.api.http) = {
      get : "/example-messages/{id}"
    };
```
といった定義が必要で、これを使うには
```
import "google/api/annotations.proto";
```
が必要らしいという理解なのだけど、これをビルドしようとすると
```
event.proto:6:1: Import "google/api/annotations.proto" was not found or had errors.
```
というエラーが出てしまう。

こういうところで躓くの嫌すぎる。
