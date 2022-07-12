---
title: "GoTrue"
date: "2022-07-12"
tags: ["supabase"]

---

supabaseで使っている認証モジュールが[netlify/gotrue: An SWT based API for managing users and issuing SWT tokens](https://github.com/netlify/gotrue)。

supabaseのAPIでGoは提供されてないので、直接たたけないか調べてみる。

[Architecture | Supabase](https://supabase.com/docs/architecture)見ると、`/auth`でGoTrueに流されるようだが、Kongの公開ポート`54321`経由で`http://localhost:54321/auth`を叩いても、`{"message":"no Route matched with those values"}`とのこと。

kongのコンテナの`/home/kong/kong.yml`に設定が書いてあった。

`http://localhost:54321/auth/v1/settings`をブラウザで開くと`No API key found in request.`のエラー。

