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

APIキーは、supabase起動時に表示されている奴だろうか。

[API Key Authentication to Secure Server Endpoint | Kong Inc.](https://konghq.com/blog/kong-gateway-key-authentication)を見ると`x-api-key`ヘッダにつければ良さそうだけど、
```sh
$ curl -H 'x-api-key:eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZS1kZW1vIiwicm9sZSI6InNlcnZpY2Vfcm9sZSJ9.vI9obAHOGyVVKa3pD--kJlyxp-Z2zV9UUMAhKpNLAcU' http://localhost:54321/auth/v1/settings
{
  "message":"No API key found in request"
}
```
変わらず。

[Key Authentication plugin | Kong Docs](https://docs.konghq.com/hub/kong-inc/key-auth/)には`apikey`クエリの例が出ていたのでやってみる。
```
$ curl 'http://localhost:54321/auth/v1/settings?apikey=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZS1kZW1vIiwicm9sZSI6ImFub24ifQ.625_WdcF3KHqz5amU0x2X5WWHP-OEs_4qj0ssLNHzTs' | jq .
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   428  100   428    0     0  53500      0 --:--:-- --:--:-- --:--:-- 53500
{
  "external": {
    "apple": false,
    "azure": false,
    "bitbucket": false,
    "discord": false,
    "github": false,
    "gitlab": false,
    "keycloak": false,
    "google": false,
    "linkedin": false,
    "facebook": false,
    "notion": false,
    "spotify": false,
    "slack": false,
    "workos": false,
    "twitch": false,
    "twitter": false,
    "email": true,
    "phone": true,
    "saml": false,
    "zoom": false
  },
  "external_labels": {},
  "disable_signup": false,
  "mailer_autoconfirm": true,
  "phone_autoconfirm": true,
  "sms_provider": ""
}
```
できた。

これでGoから操作する道筋が見えた気がする。
