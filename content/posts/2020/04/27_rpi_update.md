---
title: "はじめてのrpi-update"
date: "2020-04-27"
tags: ["raspberry-pi"]
---

snapを導入してみたところ、実行時にエラーが出る。
```
$ hello-world
ERROR: ld.so: object '/usr/lib/arm-linux-gnueabihf/libarmmem-${PLATFORM}.so' from /etc/ld.so.preload cannot be preloaded (cannot open shared object file): ignored.
Hello World!
```
実行自体はできているっぽいんだけど、気になるのでググったら`rpi-update`を実行すると解消するかもしれないということで、やってみた。

```
#############################################################
WARNING: 'rpi-update' updates to pre-releases of the linux 
kernel tree and Videocore firmware.

'rpi-update' should only be used if there is a specific 
reason to do so - for example, a request by a Raspberry Pi 
engineer.

DO NOT use 'rpi-update' as part of a regular update process.

##############################################################
Would you like to proceed? (y/N)
```
こんな警告出る。まあそんなに気軽にやるものではないよね、`Y`

そしてreboot。

・・・解消しない。

```
$ ls -l /usr/lib/arm-linux-gnueabihf/libarmmem-*
lrwxrwxrwx 1 root root    16  4月 30  2019 /usr/lib/arm-linux-gnueabihf/libarmmem-aarch64.so -> libarmmem-v7l.so
-rw-r--r-- 1 root root  9512  4月 30  2019 /usr/lib/arm-linux-gnueabihf/libarmmem-v6l.so
-rw-r--r-- 1 root root 17708  4月 30  2019 /usr/lib/arm-linux-gnueabihf/libarmmem-v7l.so
lrwxrwxrwx 1 root root    16  4月 30  2019 /usr/lib/arm-linux-gnueabihf/libarmmem-v8l.so -> libarmmem-v7l.so
$ uname -a
Linux raspberrypi 4.19.115-v7l+ #1305 SMP Fri Apr 17 11:59:28 BST 2020 armv7l GNU/Linux
```
`v7l`っての使ってくれればいいと思うんだけど。
