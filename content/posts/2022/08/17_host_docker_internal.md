---
title: "host.docker.internalとlinux"
date: "2022-08-17"
tags: ["docker"]

---

Docker Desktopでは、`host.docker.internal`で母艦のIPアドレスが参照できるようになっているのだけど、Docker DesktopではないLinux環境だと使えない。

で、とりあえず`172.17.0.1`でやってたりするのだけど、これだとうまくいかないときがあるっぽい。

推測調なのは、まだ手元で再現できていないから。

複数のdocker composeをまたいで通信するときに片方向になるというか。

もしかしたらDocker Engineのバージョンにもよるのかもしれない。

今度時間があるときに詳細に調べたい。
