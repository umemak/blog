---
title: "ラズパイ4導入"
date: "2020-04-17"
tags: ["raspberry-pi"]
---

以前から興味があったラズパイについに手を出しました。
4Bの4GB版。

さっそくSDカードにOSを入れて、と思ったらChromebookでできない。
https://www.raspberrypi.org/downloads/ の`Raspberry Pi Imager for Ubuntu`を入れて、起動はするもののSDカードを認識してくれないので書き込み先が指定できず。

開発者モードにすればいけるのかもしれないけれど、いったん諦めてWindows10で。
あっさり認識してOS入りSDカード作成完了。

ラズパイ起動したら、ネットワーク設定やらアップデートやらをした後、Raspberry Piの設定→インターフェイス→SSHとVNCを有効にして再起動。

これでChromebookからSSH接続とVNC接続ができるようになった。

後日、開発者モードにして試してみたところ、ターミナルで`/dev/mmcblk0`が見えるようになって、`dd`コマンドで書き込むことができた。
ImagerはLinuxアプリのせいか、見えないまま。

更に・・公式手順が示されていた（リカバリーツールを使って書き込む）
https://www.raspberrypi.org/documentation/installation/installing-images/chromeos.md
