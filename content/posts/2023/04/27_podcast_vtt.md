---
title: "Podcastのテキスト化"
date: "2023-04-27"
tags: []

---

[ポッドキャストをAIで書き起こし「LISTEN」　近藤淳也氏が立ち上げ - ITmedia NEWS](https://www.itmedia.co.jp/news/articles/2304/26/news156.html)

技術的には[Rebuild - Podcast by Tatsuhiko Miyagawa](https://rebuild.fm/search)で見たことある感じだったけど、これ登録されてるPodcastの横断検索出来たらすごく便利なサービスかもしれない。

mp3ダウンロードして、[VOSK Offline Speech Recognition API](https://alphacephei.com/vosk/)とかでテキスト化して、の前にタイムスタンプ情報が欲しいからVTT化ができるといいな、だれか作ってないかな。

ググったら[MaxVRAM/Vosk-VTT-Client: Client for Vosk voice-to-text server, sending real-time transcriptions to remote OSC receiver.](https://github.com/MaxVRAM/Vosk-VTT-Client)がヒットしたけどどうだろう。

VTTに出来たら、あとはプレーヤーと連携させれば良い。
なんか作りかけてた気もするけど、たしかNext.jsで画面作ろうとしてモジュール化とかが面倒で投げた記憶が。。。

またやり直してみようかな。
