---
title: "Firebase v9 SDK"
date: "2022-01-10"

---

FirebaseのAuth組み込み、参考にしているWebサイトの例が
```
import firebase from "firebase";

firebase.auth().hogehoge
```
で、真似して実装しても
```
This dependency was not found:

* firebase in ./src/router/index.js

To install it, you can run: npm install --save firebase
```
エラーになって悩んでいた。

結局、
```
import { getAuth } from "firebase/auth";

getAuth().hogehoge
```
で書くと通ることに気づいた。

これはJavaScript モジュール形式の Firebase JS SDK バージョン 9（v9 SDK）というものらしい。

https://firebase.google.com/docs/web/setup?hl=ja#add-sdks-initialize

たしかにインストールしたSDKは、firebase@9.6.2 だった。

古い書き方から移行する手順もちゃんと用意されていた。

https://firebase.google.com/docs/web/modular-upgrade?authuser=0#about_the_compat_libraries

マニュアルちゃんと読まないと無駄に時間を消費するという例でした。
