---
title: "Expo"
date: "2022-05-31"
tags: ["expo"]

---

以前一度使ってみたことがある[Expo](https://expo.dev/)に再入門。

[前にやったとき](https://umemak.github.io/blog/posts/2020/07/22_raspi_expo/)はWSLだとダメでラズパイで動かしていたけど、もう１年以上たっているしいけるのでは？という期待を込めてWSL2でやってみる。

```sh
$ sudo npm install --global expo-cli
$ expo init .
✔ Choose a template: › tabs (TypeScript)   several example screens and tabs using react-navigation and TypeScript
✔ Downloaded template.
📦 Using npm to install packages.
✔ Installed JavaScript dependencies.

✅ Your project is ready!

To run your project, run one of the following npm commands.

- npm start # you can open iOS, Android, or web from here, or run them directly with the commands below.
- npm run android
- npm run ios # requires an iOS device or macOS for access to an iOS simulator
- npm run web
Project is already inside of a git repo, skipping git init.

$ npm start

> photomap@1.0.0 start
> expo start

Starting project at /home/umemak/workspace/photomap
Starting Metro Bundler

› Metro waiting on exp://127.0.0.1:19000
› Scan the QR code above with Expo Go (Android) or the Camera app (iOS)

› Press a │ open Android
› Press w │ open web

› Press r │ reload app
› Press m │ toggle menu

› Press ? │ show all commands

Logs for your project will appear below. Press Ctrl+C to exit.
✔ It looks like you're trying to use web support but don't have the required dependencies installed. Would you like to install
webpack-dev-server@~3.11.0, @expo/webpack-config@~0.16.2? … yes

✔ Installed webpack-dev-server@~3.11.0, @expo/webpack-config@~0.16.2
CommandError: Missing package "webpack-dev-server" in the project. Try running the command again. (cwd: /home/umemak/workspace/photomap)
```
Expo GoでQRスキャンしても、LAN内のIPアドレス指定してマニュアル接続してみても接続できなかった。

もうちょっと調べる。
