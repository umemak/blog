---
title: "Flutter 3をインストールしてみる"
date: "2022-05-13"
tags: ["flutter"]

---

WSL2にインストールしてみる。

[Linux install | Flutter](https://docs.flutter.dev/get-started/install/linux)

```sh
$ cd ~/sdk
$ git clone https://github.com/flutter/flutter.git -b stable
$ export PATH="$PATH:`pwd`/flutter/bin"
$ flutter doctor

Missing "unzip" tool. Unable to extract Dart SDK.
Consider running "sudo apt-get install unzip".

$ sudo apt-get install unzip
$ flutter doctor
[✓] Flutter (Channel stable, 3.0.0, on Ubuntu 20.04 LTS 5.10.16.3-microsoft-standard-WSL2, locale C.UTF-8)
[✗] Android toolchain - develop for Android devices
    ✗ Unable to locate Android SDK.
      Install Android Studio from: https://developer.android.com/studio/index.html
      On first launch it will assist you in installing the Android SDK components.
      (or visit https://flutter.dev/docs/get-started/install/linux#android-setup for detailed instructions).
      If the Android SDK has been installed to a custom location, please use
      `flutter config --android-sdk` to update to that location.

[✗] Chrome - develop for the web (Cannot find Chrome executable at google-chrome)
    ! Cannot find Chrome. Try setting CHROME_EXECUTABLE to a Chrome executable.
[☠] Linux toolchain - develop for Linux desktop (the doctor check crashed)
    ✗ Due to an error, the doctor check did not complete. If the error message below is not helpful, please let us know about this issue
      at https://github.com/flutter/flutter/issues.
    ✗ ProcessException: Failed to find "pkg-config" in the search path.
        Command: pkg-config 
[!] Android Studio (not installed)
[✓] Connected device (1 available)
[✓] HTTP Host Availability

! Doctor found issues in 4 categories.
```
とりあえず本体は入ったのでヨシ。

以前作りかけのリポジトリが動くか試してみる。
```sh
$ cd ../workspace/flutter_quiz/
$ flutter run -d web-server --web-hostname 0.0.0.0 --web-port 3000 --web-renderer html
Downloading Web SDK...                                              4.2s
Downloading CanvasKit...                                         1,018ms
Running "flutter pub get" in flutter_quiz...                        3.3s
Launching lib/main.dart on Web Server in debug mode...
Waiting for connection from debug service on Web Server...         14.7s
lib/main.dart is being served at http://0.0.0.0:3000
The web-server device requires the Dart Debug Chrome extension for debugging. Consider using the Chrome or Edge devices for an improved
development workflow.

🔥  To hot restart changes while running, press "r" or "R".
For a more detailed help message, press "h". To quit, press "q".
```

http://0.0.0.0:3000 で表示できた。
