---
title: "CORS対応"
date: "2022-10-08"
tags: ["chi"]

---

openapi-generator-cliのtypescript-axiosで生成したクライアントでConfigureにaccessTokenをセットして取得APIを叩いたらうまく通信できなかった。

API側のログにはOPTIONSのリクエストが来ていて、200で返している。

chiのcors.OptionsのAllowedMethodsにOPTIONSは入っているので、これは想定通り。なのにそのあとのGETリクエストが来ていない。

[Bearer認証付きAPIでCORSエラーとたたかった記録 - Qiita](https://qiita.com/kurab/items/84573b3092c8db4ba750)に答えが書いてあった。

cors.OptionsにAuthorization入りのAllowedHeadersを追加で入れたら解決した。
