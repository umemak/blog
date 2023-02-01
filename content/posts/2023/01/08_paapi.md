---
title: "PA-API使ってみる"
date: "2023-01-08"
tags: ["amazon"]

---

[「読んだ本」をObsidianで管理する｜masuipeo｜note](https://note.com/masuipeo/n/n69faf66a0f10)で書かれている、PA-API（Product Advertising API）を使って情報取得をしてみようとした。

アソシエイトIDはだいぶ前に取得してあったので、それを使用して認証キーの発行はできた。

- [【Amazon API】アクセスキーID・シークレットキー・アソシエイトタグの確認方法](https://blog-and-destroy.com/14353)

で、Node.jsのSDKをダウンロードしてサンプルを実行してみたら、エラー。
```text
Status Code: 429
Error Object: "{\"__type\":\"com.amazon.paapi5#TooManyRequestsException\",\"Errors\":[{\"Code\":\"TooManyRequests\",\"Message\":\"The request was denied due to 
request throttling. Please verify the number of requests made per second to the Amazon Product Advertising API.\"}]}"
```

売り上げがないと使えないらしい。。

- [Amazonアソシエイトの「Too Many Requests」エラーの原因は売上不足 | どぎブロ](https://doggy-kbk12.com/too-many-requests/)
