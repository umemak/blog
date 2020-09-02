---
title: "Flutterに入門"
date: "2020-09-02"
tags: ["flutter"]
---

Surface Go 2 に Flutter Web 環境をインストールしたのでメモ。

基本的には[公式手順](https://flutter.dev/docs/get-started/install)に沿って進める。

* gitからclone
```
$ cd ~/workspace
$ git clone https://github.com/flutter/flutter.git -b stable
```

* 環境変数PATHに追加
ユーザー環境変数の最後に追加した

* flutter doctor実行
```
[√] Flutter (Channel stable, 1.20.2, on Microsoft Windows [Version 10.0.19041.450], locale ja-JP)
[X] Android toolchain - develop for Android devices
    X Unable to locate Android SDK.
      Install Android Studio from: https://developer.android.com/studio/index.html
      On first launch it will assist you in installing the Android SDK components.
      (or visit https://flutter.dev/docs/get-started/install/windows#android-setup for detailed instructions).
      If the Android SDK has been installed to a custom location, set ANDROID_SDK_ROOT to that location.
      You may also want to add it to your PATH environment variable.

[!] Android Studio (not installed)
[!] VS Code (version 1.48.2)
    X Flutter extension not installed; install from
      https://marketplace.visualstudio.com/items?itemName=Dart-Code.flutter
[!] Connected device
    ! No devices available
```
この時点ではこれでOK

* Web設定
https://flutter.dev/docs/get-started/web の手順を実行
```
$ flutter channel beta
$ flutter upgrade
$ flutter config --enable-web
$ flutter devices

Web Server (web) • web-server • web-javascript • Flutter Tools
Chrome (web)     • chrome     • web-javascript • Google Chrome 84.0.4147.135
Edge (web)       • edge       • web-javascript • Microsoft Edge 81.0.416.88
```

* VSCodeにFlutter拡張機能をインストール

* doctor再実行
```
[√] Flutter (Channel beta, 1.21.0-9.2.pre, on Microsoft Windows [Version 10.0.19041.450], locale ja-JP)
[X] Android toolchain - develop for Android devices
    X Unable to locate Android SDK.
      Install Android Studio from: https://developer.android.com/studio/index.html
      On first launch it will assist you in installing the Android SDK components.
      (or visit https://flutter.dev/docs/get-started/install/windows#android-setup for detailed instructions).
      If the Android SDK has been installed to a custom location, set ANDROID_SDK_ROOT to that location.
      You may also want to add it to your PATH environment variable.

[√] Chrome - develop for the web
[!] Android Studio (not installed)
[√] VS Code (version 1.48.2)
[√] Connected device (3 available)
```

* アプリ作成
```
$ flutter create myflutterwebapp
$ cd myflutterwebapp
```

* アプリ実行
```
$ flutter run -d chrome
```
Chromeが起動して、カウンターアプリが表示された。

* アプリのビルド
```
$ flutter build web
```
`build/web/`にファイルが作成される。

* ビルドしたアプリの確認
npmの`http-server`を利用。事前にnpmのインストールはしてある前提で。
```
$ cd build/web/
$ npx http-server
```
`Hit CTRL-C to stop the server`のメッセージが出たら、ブラウザで http://localhost:8080 にアクセス。`flutter run`で実行したときと同じカウンターアプリが表示される。

ということで、思ったより簡単に環境構築ができた。
Flutterは気になっていたけれども、Android StudioとかSDKとかセットアップするのが大変そうだったので敬遠していた。
FLutter Web（まだベータ版）の登場で、気軽に体験できるようになったのは良いと思う。
