---
title: "Vosk使ってみる2"
date: "2022-10-20"
tags: ["Vosk", "python"]

---

node.jsで使うのあきらめて、Pythonで試してみた。
- [vosk-api/test_microphone.py at master · alphacep/vosk-api](https://github.com/alphacep/vosk-api/blob/master/python/example/test_microphone.py)

あっさり使えた。

ついでに、[3 分で作る無料の翻訳 API with Google Apps Script - Qiita](https://qiita.com/tanabee/items/c79c5c28ba0537112922)を参考に、日本語→英語翻訳APIを立てて連携してみた。

Pythonを理解するのにちょっと手間取ったけど、意外とすんなりリアルタイム音声認識＆翻訳が出来上がってびっくりした。

