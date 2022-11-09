---
title: "ラズパイをルーターにする"
date: "2022-11-09"
tags: ["raspberry-pi"]

---

PCは昨日買ってきたLANケーブルでインターネット接続は解決した。

Pixel4も同じ現象だった。

LANケーブルつないだらいけるのか、LANポート付きUSB-HUBを試してみたけれど、ダメだった。

なので、ラズパイを無線LANルーターにしてみることにした。

やり方はググったらいくつか出てきた。

- [ラズパイを無線LANルーター化する ～アクセスポイント編～：名刺サイズの超小型PC「ラズパイ」で遊ぶ（第24回）（1/2 ページ） - ITmedia NEWS](https://www.itmedia.co.jp/news/articles/2008/14/news042.html)
- [Raspberry Piで無線LANルーター（AP）を作る](https://it-syoya-engineer.com/raspberry-pi-router/)
- [ex2.RaspberryPiを無線LANアクセスポイント化する - RaspberryPiで各種サーバー作り！ - ある阪大生の物置小屋](https://kassyjp.ninja-web.net/ras/jessie/bridge.htm)
- [Raspberry Pi WiFiアクセスポイント&ルーター化 - みかんのゆるふわ技術ブログ](https://www.mikan-tech.net/entry/raspi-ap-sta-router)
- [Raspberry Pi Documentation - Configuration](https://www.raspberrypi.com/documentation/computers/configuration.html#setting-up-a-routed-wireless-access-point)

ルーター用にするOSもあるみたいだけど、イメージ作るの面倒なのでいったんパス。

- [ラズパイがファイアウォール付き無線LANルーターに変身、「LEDE」で簡単に | 日経クロステック（xTECH）](https://xtech.nikkei.com/it/atcl/column/17/041900152/091400022/)
- [Raspberry Pi 3をOpenWrtで無線LANルータ化した - にゃののん日記](https://nyanonon.hatenablog.com/entry/20190531/1559313000)


ざっと眺めて、[Raspberry Piで無線LANルーター（AP）を作る](https://it-syoya-engineer.com/raspberry-pi-router/)を基本にやってみた。

途中、iptables がインストールされていなかったので追加でインストールした。
```sh
sudo apt-get install iptables-persistent
```

最後までやってみたけど、SSIDが見つからない。。
