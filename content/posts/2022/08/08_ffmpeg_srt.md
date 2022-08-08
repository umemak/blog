---
title: "FFmpegで字幕"
date: "2022-08-08"
tags: ["ffmpeg"]

---

動画の音声を[Amazon Transcribe（音声をテキストに変換する機能を簡単に追加）| AWS](https://aws.amazon.com/jp/transcribe/)でsrt形式の日本語文字起こしをして、DockerのUbuntuにインストールしたFFmpegで動画に字幕を焼きこもうとした。

日本語文字が豆腐になってしまった。

日本語フォントとかインストールしてやらないとダメなのか。。

[できた](https://github.com/umemak/ffmpeg_test/blob/main/Dockerfile)
