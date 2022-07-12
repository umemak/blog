---
title: "supabaseを試す"
date: "2022-07-11"
tags: ["supabase"]

---

以前調べたとき、ローカルで動かしたときにAuth系はサポートしてないというような記事を見て、残念に思っていたのだけれど、Kuzzleの認証も思ったのと違う感じで。

- [With Docker | Supabase](https://supabase.com/docs/guides/hosting/docker)
- [Supabaseをローカル環境に構築してNext.jsアプリで利用する（前半）](https://zenn.dev/hrtk/articles/supabase-nextjs-local)

このあたりを見ると、なんかできそう。しかもDockerで。

```sh
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
$ echo 'eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"' >> /home/umemak/.profile
$ eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"
$ brew install supabase/tap/supabase
$ supabase help
Supabase CLI 0.29.1
 :
$ supabase init
$ supabase start
```
http://localhost:54323/ でダッシュボードが表示された。
