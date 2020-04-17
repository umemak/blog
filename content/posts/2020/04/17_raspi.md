---
title: "ラズパイ4導入"
date: "2020-04-17"
tags: ["raspi"]
---

以前から興味があったラズパイについに手を出しました。
4Bの4GB版。

さっそくSDカードにOSを入れて、と思ったらChromebookでできない。
https://www.raspberrypi.org/downloads/ の`Raspberry Pi Imager for Ubuntu`を入れて、起動はするもののSDカードを認識してくれないので書き込み先が指定できず。

開発者モードにすればいけるのかもしれないけれど、いったん諦めてWindows10で。
あっさり認識してOS入りSDカード作成完了。

ラズパイ起動したら、ネットワーク設定やらアップデートやらをした後、Raspberry Piの設定→インターフェイス→SSHとVNCを有効にして再起動。

これでChromebookからSSH接続とVNC接続ができるようになった。

