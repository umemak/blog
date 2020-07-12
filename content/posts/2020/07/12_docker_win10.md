---
title: "Windows10にDocker Desktopをインストール"
date: "2020-07-12"
tags: ["win10", "docker"]
---

最初にSurface Go2をセットアップしたとき、WSL2のほうにDockerをインストールしていた。
使う時だけ起動すればいいと思っていたが、意外と面倒（sudoしてデーモン起動させるのとか）に感じていた。

[VSCode blogの記事](https://code.visualstudio.com/blogs/2020/07/01/containers-wsl)を見て、Windows側にDocker Desktopをインストールするのもありかと思い、やってみた。

インストール自体は特に問題なく完了。リモートコンテナ接続もOK。
気になっていた負荷も、Docker起動時にシステム全体重くなるのは想定の範囲内。
起動してしまえばそれほど。

しばらく使ってみようと思う。
