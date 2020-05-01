---
title: "ラズパイでdroidcam"
date: "2020-05-01"
tags: ["raspberry-pi"]
---

ラズパイにWebカメラ付けてみたくても売っていないので、Android端末をカメラ化する。

Android端末側にはアプリをインストールしておく。

ラズパイ側。公式ページにはLinux用のインストール方法が用意されているが、
http://www.dev47apps.com/droidcam/linuxx/
> Note: 32-bit binaries are no longer provided, you’ll need to compile the client from source.
この条件に該当するのでソースからインストールする。

```
mkdir workspace
cd workspace
git clone https://github.com/libjpeg-turbo/libjpeg-turbo.git
cd libjpeg-turbo/
sudo apt install cmake
cmake -G"Unix Makefiles"
make
sudo make install
ls /opt/libjpeg-turbo/
cd ..
git clone https://github.com/aramg/droidcam.git
cd droidcam/linux/
sudo apt install gtk+-2.0 libavutil-dev libswscale-dev
sudo apt install raspberrypi-kernel-headers
make
sudo ./install 
lsmod | grep v4l2loopback_dc
./droidcam-cli {Android端末のIPアドレス} {Android端末のdroidcamポート}
```
この状態で、VLCでキャプチャデバイスを開く→`/dev/video0`選択でAndroidのカメラ映像が表示される。
