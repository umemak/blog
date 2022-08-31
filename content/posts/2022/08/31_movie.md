---
title: "動画編集のフロー"
date: "2022-08-31"
tags: []

---

何となく見えてきた。

1. Shotcutで動画を読み込んで、mp3で音声を書き出す
2. 書き出したmp3をS3にアップロードする
3. Amazon TranscribeでVTTファイルを作成する
4. VTTファイルをマーカーとみなしたMLTを作成する
5. Shotcutで編集して動画をmp4で書き出す
6. MLTのマーカーからVTTを出力する
7. ffmpegでmp4とVTTを合成する
