---
title: "VOICEVOX"
date: "2022-03-02"

---

Docker Desktopもインストールしたので、最近話題の[VOICEVOX | 無料で使える中品質なテキスト読み上げソフトウェア](https://voicevox.hiroshiba.jp/)を試してみた。

```sh
$ docker run -it --rm -p 50021:50021 hiroshiba/voicevox_engine:cpu-ubuntu20.04-latest
```

最初、[GoとDockerでつくる音声合成CLI](https://zenn.dev/nobonobo/articles/60fe0cd1a5af74?utm_source=pocket_mylist)のページを参考にしてバージョン指定してたけど、latestにしたら使えるキャラクターが増えた。つい最近追加されたらしい。

上記ページを参考に、スクリプト作って、生成されたwavファイルをメディアプレーヤーで再生。

```sh
#!/bin/sh
TXT=`cat hello.txt`
curl -s -XPOST -G "http://localhost:50021/audio_query?speaker="$1 --data-urlencode text=$TXT \
| curl -s -XPOST "http://localhost:50021/synthesis?speaker="$1 \
-H 'accept: audio/wav' -H 'Content-Type: application/json' -d @- \
> hello.wav
```

テキストファイル監視して保存したら再生されるみたいな仕組み作れそうだけど、時間あるときにやるネタにしておこう。。
