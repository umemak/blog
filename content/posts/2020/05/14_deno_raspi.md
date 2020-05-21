---
title: "ラズパイでDenoを動かしてみる"
date: "2020-05-14"
tags: ["raspberry-pi", "deno"]
draft: true
---

https://deno.land/#installation
オフィシャルのインストーラーだと、arm用のバイナリが提供されていないので、ビルドする。

https://qiita.com/kt3k/items/0267c355997fc1a0539f
参考に。

rustが入っていなかったので、インストール
https://qiita.com/tkyonezu/items/7e190fd03bfe95692e75
```
$ curl https://sh.rustup.rs -sSf | sh
```
`1) Proceed with installation (default)`を選択。
実行後に再ログイン。

```
$ git clone https://github.com/denoland/deno.git
$ cd deno
$ git submodule update --init
$ cargo build
```

```
   Compiling string_cache_codegen v0.5.1
error: failed to run custom build command for `rusty_v8 v0.4.2`

Caused by:
  process didn't exit successfully: `/home/pi/workspace/deno/target/debug/build/rusty_v8-9fb06926524ad477/build-script-build` (exit code: 101)
--- stdout
static lib URL: https://github.com/denoland/rusty_v8/releases/download/v0.4.2/librusty_v8_debug_arm-unknown-linux-gnueabihf.a
cargo:rustc-link-search=/home/pi/workspace/deno/target/debug/gn_out/obj
Downloading https://github.com/denoland/rusty_v8/releases/download/v0.4.2/librusty_v8_debug_arm-unknown-linux-gnueabihf.a
Downloading https://github.com/denoland/rusty_v8/releases/download/v0.4.2/librusty_v8_debug_arm-unknown-linux-gnueabihf.a...
HTTP Error 404: Not Found

--- stderr
Traceback (most recent call last):
  File "./tools/download_file.py", line 63, in <module>
    sys.exit(main())
  File "./tools/download_file.py", line 58, in main
    DownloadUrl(args.url, f)
  File "./tools/download_file.py", line 44, in DownloadUrl
    raise e
urllib2.HTTPError: HTTP Error 404: Not Found
thread 'main' panicked at 'assertion failed: status.success()', /home/pi/.cargo/registry/src/github.com-1ecc6299db9ec823/rusty_v8-0.4.2/build.rs:229:5
note: run with `RUST_BACKTRACE=1` environment variable to display a backtrace

warning: build failed, waiting for other jobs to finish...
error: build failed
```
うーん。
なにか足りないらしい。
`librusty_v8_debug_aarch64-unknown-linux-gnu.a`ってのを使ってくれればいいのに。。

librusty_v8もビルドしてみる
```
$ git clone https://github.com/denoland/rusty_v8.git
$ cd rusty_v8
$ git submodule update --init --recursive
$ V8_FROM_SOURCE=1 cargo build -vv
```
```
[rusty_v8 0.4.2] gn gen --root=/home/pi/workspace/rusty_v8 /home/pi/workspace/rusty_v8/target/debug/gn_out
[rusty_v8 0.4.2] running: "/home/pi/workspace/rusty_v8/target/debug/ninja_gn_binaries-20200506/linux64/gn" "--root=/home/pi/workspace/rusty_v8" "gen" "/home/pi/workspace/rusty_v8/target/debug/gn_out" "--args=is_debug=true clang_base_path=\"/home/pi/workspace/rusty_v8/target/debug/clang\""
[rusty_v8 0.4.2] /home/pi/workspace/rusty_v8/target/debug/ninja_gn_binaries-20200506/linux64/gn: 1: /home/pi/workspace/rusty_v8/target/debug/ninja_gn_binaries-20200506/linux64/gn: Syntax error: "(" unexpected
[rusty_v8 0.4.2] thread 'main' panicked at '
[rusty_v8 0.4.2] command did not execute successfully, got: exit code: 2
[rusty_v8 0.4.2] 
[rusty_v8 0.4.2] build script failed, must exit now', /home/pi/.cargo/registry/src/github.com-1ecc6299db9ec823/cargo_gn-0.0.15/src/lib.rs:203:3
[rusty_v8 0.4.2] note: run with `RUST_BACKTRACE=1` environment variable to display a backtrace
error: failed to run custom build command for `rusty_v8 v0.4.2 (/home/pi/workspace/rusty_v8)`

Caused by:
  process didn't exit successfully: `/home/pi/workspace/rusty_v8/target/debug/build/rusty_v8-fc83b85a6fe02870/build-script-build` (exit code: 101)
--- stdout
Downloading https://github.com/denoland/ninja_gn_binaries/archive/20200506.tar.gz... Done.
using Chromiums clang
clang_base_path /home/pi/workspace/rusty_v8/target/debug/clang
Downloading https://commondatastorage.googleapis.com/chromium-browser-clang/Linux_x64/clang-n346557-4e0d9925-3.tgz .......... Done.
cargo:warning=Not using sccache
The current directory is /home/pi/workspace/rusty_v8
gn gen --root=/home/pi/workspace/rusty_v8 /home/pi/workspace/rusty_v8/target/debug/gn_out
running: "/home/pi/workspace/rusty_v8/target/debug/ninja_gn_binaries-20200506/linux64/gn" "--root=/home/pi/workspace/rusty_v8" "gen" "/home/pi/workspace/rusty_v8/target/debug/gn_out" "--args=is_debug=true clang_base_path=\"/home/pi/workspace/rusty_v8/target/debug/clang\""

--- stderr
/home/pi/workspace/rusty_v8/target/debug/ninja_gn_binaries-20200506/linux64/gn: 1: /home/pi/workspace/rusty_v8/target/debug/ninja_gn_binaries-20200506/linux64/gn: Syntax error: "(" unexpected
thread 'main' panicked at '
command did not execute successfully, got: exit code: 2

build script failed, must exit now', /home/pi/.cargo/registry/src/github.com-1ecc6299db9ec823/cargo_gn-0.0.15/src/lib.rs:203:3
note: run with `RUST_BACKTRACE=1` environment variable to display a backtrace
```
Syntax errorって。。

sudo apt install clang -y
