---
title: "MLTファイルを作る"
date: "2022-08-11"
tags: ["go"]

---

Shotcutのプロジェクトの保存形式がMLTで、中身はXMLのテキスト。

作業動画を編集していて、無音部分はスキップして尺を短くしたい。

無音部分はffmpegの[silencedetect](https://ffmpeg.org/ffmpeg-filters.html#silencedetect)で検出できるので、そのタイムスタンプで切ったShotcutプロジェクトを開けば、効率的に不要な部分を切り詰めつつ必要な部分を残せるのではないかという目論見。

https://github.com/umemak/ffmpeg_test/blob/main/main.go

とりあえずこんな感じで。
