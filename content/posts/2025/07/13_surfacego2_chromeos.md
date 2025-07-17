---
title: "Surface go 2にChromeOSをインストールする"
date: "2025-07-13"
tags: ["Surface", "ChromeOS"]

---

Surface go 2の動作が重いしバッテリーの持ちがカンファレンス1日持たなくなってきたので、なんとかしたいと思い、ChromeOS Flexを試してみた。

[ChromeOS Flex インストール ガイド](https://support.google.com/chromeosflex/answer/11541904?hl=ja)に沿って実行したらとくに問題なく完了できた。

USBからのブートは、Windowsの設定で変更できた。

Linux入れて、VS Code入れて、npm入れて、Claude Code入れるところまでやってVS Codeの日本語フォントが明朝なのが気になってUDEV Gothicを入れたけど反映されず。
→`/usr/local/share/fonts/`にttfファイルを置いたら反映された。

あとVS CodeのターミナルでコピペのキーボードショートカットがShiftも押さないとダメなのが気になる（エディタではShiftいらない）。
→VS Codeではなく、ターミナルの設定で変更できた

動作は軽くなったので、しばらくこれでやってみようと思う。
