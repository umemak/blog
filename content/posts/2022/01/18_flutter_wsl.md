---
title: "続・FlutterをWSL2で開発したい"
date: "2022-01-18"

---

昨日調べた中で手っ取り早そうな、デバイスは実機を使うパターンを試してみた。

VS CodeでFlutterデバッグ動かすところまでは行けたけど、デバイスの接続でエラーになってしまう。

```
$ adb pair <ipaddress>:<port>
Enter pairing code: <code>
Failed: Unable to start pairing client.
```

ping打っても`Destination Host Unreachable`だし、WindowsのFirewall一時的にオフにしても変わらず。

同じネットワークだと思うんだけどなぁ。。IPアドレスも連番だし。
