---
title: "ワイヤレスデバッグの接続ができないとき"
date: "2022-01-20"

---

Pixel4でAndroid12の時の現象。ほかの組み合わせは未確認。

Androidのワイヤレスデバッグを使おうとして
```
$ adb pair 192.168.***.***:nnnnn
Enter pairing code: 999999
Failed: Unable to start pairing client.
```
こんなエラーになったとき

```
$ ping 192.168.***.***
PING 192.168.***.*** (192.168.***.***) 56(84) bytes of data.
From 192.168.***.*** icmp_seq=3 Destination Host Unreachable
^C
--- 192.168.***.*** ping statistics ---
4 packets transmitted, 0 received, +1 errors, 100% packet loss, time 3093ms
```
pingも通らないなら

デバイスを再起動すると直る。
