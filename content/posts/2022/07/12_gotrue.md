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

```sh
$ curl -v -X POST -H 'Content-Type: application/json' --data '{"email": "email@example.com","password": "secret"}' 'http://localhost:54321/auth/v1/signup?apikey=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZS1kZW1vIiwicm9sZSI6ImFub24ifQ.625_WdcF3KHqz5amU0x2X5WWHP-OEs_4qj0ssLNHzTs'
{"access_token":"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhdWQiOiJhdXRoZW50aWNhdGVkIiwiZXhwIjoxNjU3NjMxMTgxLCJzdWIiOiI2MzNjOTNhMS0xNDdkLTQwZDUtOWRhOC1iMDdhNjMwNjA5MTEiLCJlbWFpbCI6ImVtYWlsQGV4YW1wbGUuY29tIiwicGhvbmUiOiIiLCJhcHBfbWV0YWRhdGEiOnsicHJvdmlkZXIiOiJlbWFpbCIsInByb3ZpZGVycyI6WyJlbWFpbCJdfSwidXNlcl9tZXRhZGF0YSI6e30sInJvbGUiOiJhdXRoZW50aWNhdGVkIn0.2f3hFbrrKrKLcBZvDVKJT4Q29RnpqvY-byx3icWQTXI","token_type":"bearer","expires_in":3600,"refresh_token":"OVY0O85jSg0vUO90U_wjEw","user":{"id":"633c93a1-147d-40d5-9da8-b07a63060911","aud":"authenticated","role":"authenticated","email":"email@example.com","email_confirmed_at":"2022-07-12T12:06:21.014989949Z","phone":"","last_sign_in_at":"2022-07-12T12:06:21.020771062Z","app_metadata":{"provider":"email","providers":["email"]},"user_metadata":{},"identities":[{"id":"633c93a1-147d-40d5-9da8-b07a63060911","user_id":"633c93a1-147d-40d5-9da8-b07a63060911","identity_data":{"sub":"633c93a1-147d-40d5-9da8-b07a63060911"},"provider":"email","last_sign_in_at":"2022-07-12T12:06:* Connection #0 to host localhost left intact
21.008247116Z","created_at":"2022-07-12T12:06:21.008442Z","updated_at":"2022-07-12T12:06:21.008449Z"}],"created_at":"2022-07-12T12:06:20.987039Z","updated_at":"2022-07-12T12:06:21.026399Z"}}
```
ユーザー作成もできた。
