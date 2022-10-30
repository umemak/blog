---
title: "ffmpegで複数言語の字幕を埋め込む"
date: "2022-10-30"
tags: ["ffmpeg"]

---

`movie.mp4`に日本語字幕`jpn.vtt`と英語字幕`eng.vtt`を埋め込んだ`out.mp4`を作成するコマンド。

```sh
ffmpeg -i 'movie.mp4' -i 'jpn.vtt' -i 'eng.vtt' \
-map 0:v -map 0:a -map 1 -map 2 \
-c:v copy -c:a copy -c:s mov_text \
-metadata:s:s:0 language=jpn \
-metadata:s:s:1 language=eng \
out.mp4
```

