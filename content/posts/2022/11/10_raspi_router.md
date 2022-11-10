---
title: "ラズパイをルーターにする2"
date: "2022-11-10"
tags: ["raspberry-pi"]

---

SSIDが見つからない件。

[linux - Raspberry Pi 4 hostapd hotspot not visible - Super User](https://superuser.com/questions/1503862/raspberry-pi-4-hostapd-hotspot-not-visible)の回答を参考に、

```sh
sudo systemctl stop dhcpcd.service
sudo systemctl restart hostapd.service
sudo systemctl start dhcpcd.service
```

したらいけた。

`/etc/dhcpcd.conf`に`denyinterfaces wlan0`を追記するのは効き目なかった。

スピードテストの結果

| 経由 | ダウンロード | アップロード | レイテンシ |
|---|--:|--:|--:|
|無線LANルーター|88.2Mbps|78.4Mbps|79ms|
|ラズパイ2.4G|32.0Mbps|27.7Mbps|5ms|
|ラズパイ5G|54.1Mbps|59.5Mbps|5ms|
|有線|91.6Mbps|60.4Mbps|4ms|

専用機にはかなわないか。。
