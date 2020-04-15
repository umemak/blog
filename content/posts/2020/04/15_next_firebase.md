---
title: "NextJSをFirebaseで使おうとして学んだこと"
date: "2020-04-15"
tags: ["nextjs", "firebase"]
draft: true
---

ここ最近、FirebaseでNextJSを使ったWebアプリを作ろうとして試行錯誤していた。
どうにもうまく行かないのでそろそろNextJSを諦めて素のReactで作り直そうと考えている。
ただ諦めるのも悔しいので、学んだことをまとめておく。

## 環境
* Chromebook + GitPod

## 要件
* Firebase認証を使ったログイン機能
* Firestoreを使ったデータ保存
* Firebase Hostingを使ったインターネット公開

## 経緯
* とりあえずNextJSのサンプルを使ってプロジェクト作成
  - https://github.com/zeit/next.js/tree/master/examples/with-typescript
* Firebase認証を実装するにあたり別のサンプルの要素を取り込む
  - https://github.com/zeit/next.js/tree/master/examples/with-firebase
  - この状態である程度動くものができて、デプロイどうするかというところで
* Firebaseを使ったサンプルもあるのを見つけたので、これを取り込み
  - https://github.com/zeit/next.js/tree/master/examples/with-firebase-hosting-and-typescript
  - ここでこのサンプルをベースに作り直していたら違った結果になったかもしれない
* 
