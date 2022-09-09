---
title: "Goで設定を良い感じに処理する方法"
date: "2022-09-09"
tags: ["go"]

---

コマンドラインで引数を処理する順番は[以前](../../2021/01/11_settings/)調べたことがあるのだけど、これをいい感じに処理してくれるGoのライブラリが欲しい気がする。

> まず設定ファイルを読み、環境変数が設定されていれば上書き、コマンドラインで指定されていればさらに上書き

- [joho/godotenv: A Go port of Ruby's dotenv library (Loads environment variables from `.env`.)](https://github.com/joho/godotenv)
- [Netflix/go-env: a golang library to manage environment variables](https://github.com/Netflix/go-env)
- [caarlos0/env: A simple and zero-dependencies library to parse environment variables into structs.](https://github.com/caarlos0/env)
- [ilyakaznacheev/cleanenv: ✨Clean and minimalistic environment configuration reader for Golang](https://github.com/ilyakaznacheev/cleanenv)
- [cristalhq/aconfig: Simple, useful and opinionated config loader.](https://github.com/cristalhq/aconfig)
- [kkyr/fig: A minimalist Go configuration library](https://github.com/kkyr/fig)

ざっと検索してこんな感じでいろいろありそうだけど、環境変数を扱うものが多い気がする。

基本的には構造体を定義して、タグで環境変数名や引数名と紐づけていくのが主流っぽい。
