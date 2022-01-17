---
title: "FlutterをWSL2で開発したい"
date: "2022-01-17"

---

ちょっと気分転換に。

Surface Go2では力不足だと思って遠慮していた、Flutterのローカル環境での開発をやりたい。

以前はFlutter Webを使っていたので、ホットリロードの恩恵が受けられずにいた。

InspironになってCore i7+16GBを手にした今、Androidエミュレータ使ってホットリロードしながらサクサク画面が作れるのではないか、と。

ただ、余計なアプリをあまりインストールしたくない気持ちもあるので、できればWSL2で何とかしたい。

ちょっとググったら、デバイスは実機を使う方法はいけるらしい。

- [WSL2でFlutter環境をできるだけクリーンに構築する(えみ) - Qiita](https://qiita.com/suruseas/items/42d5d9c5beffa6ebdd78)

日本ではまだ使えない？WSA（Windows Subsystem for Android）が使えるようになれば、これがシンプルでよさそう。

- [Android™️ 用 Windows サブシステム | Microsoft Docs](https://docs.microsoft.com/ja-jp/windows/android/wsa/)
- [Install Flutter on WSL2 and run apps directly in WSA or in a physical device using ADB. | by Adam Lahbib | Dec, 2021 | Medium](https://medium.com/@adhbbam/install-flutter-on-wsl2-and-run-apps-directly-in-wsa-or-in-a-physical-device-using-adb-3602f2053f8e)

もしかしたらWSLgで何とかならない？

- [Flutter Emulator Demo on WSLg Windows 11 - YouTube](https://www.youtube.com/watch?v=GDo83QH1f-g)


