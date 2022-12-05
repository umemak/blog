---
title: "Cython入門"
date: "2022-12-05"
tags: ["python", "cython"]

---

[CythonによるPythonの高速化!!](https://zenn.dev/timoneko/articles/805919ea14427c)をやってみた。

書かれているようにエラーが出たので、[Microsoft C++ Build Tools - Visual Studio](https://visualstudio.microsoft.com/ja/visual-cpp-build-tools/)でBuild Toolsのダウンロードをしてインストール。

C++によるデスクトップ開発を選択してインストール。1.7GBもダウンロードするのか。。

で、インストールが終わってコンパイルして実行

```sh
$ time python test.py
100000000

real    0m5.251s
user    0m0.000s
sys     0m0.000s
```

cdefを加える

```sh
$ time python test.py
100000000

real    0m0.214s
user    0m0.000s
sys     0m0.015s
```

すごい。
