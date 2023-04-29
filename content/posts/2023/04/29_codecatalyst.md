---
title: "Amazon CodeCatalyst使ってみる"
date: "2023-04-29"
tags: ["aws"]

---

[AWS上で開発環境一式、コードリポジトリからテンプレートコード、IDE、CI/CDパイプラインまでを丸ごと提供する「Amazon CodeCatalyst」が正式サービスに － Publickey](https://www.publickey1.jp/blog/23/awsidecicdamazon_codecatalyst.html)

やってみた。

Builder IDでログインを要求されたので、先日CodeWhisperer試すときに作ったのを使った。無駄にならなくてよかった。

aliasとspace nameを入力するところ、先にaliasを決めてからspace name作るうえに同じものを指定できないので、後から逆にしたいと思ってもできなかった。

とりあえずblueprintでSingle-page applicationを選択。

IAM roleはリンク開いたら作成画面に遷移するので、そのまま作成すればOK。
作成したものを選択して、Create projectする。

Code - Dev Environments で Create Dev Environment を選択、Visual Studio Codeを指定すると、PCのVS Codeからリモートで開発環境に接続できる。

npm installしてからnpm startしたら、ブラウザでReactの画面が表示された。

src/App.tsx を編集して保存したら、ブラウザ側もホットリロードされた。

思ったより簡単に始めることができたけど、Builder ID作成済みじゃなかったら面倒に思ってあきらめていたかも。

