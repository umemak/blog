---
title: "WSL2でmidi再生"
date: "2022-01-22"

---

MMLを再生するために何が必要か考えてみた。

MMLから直接再生できるのが良いけれど、大変そうなので既存の何かがあれば使っていきたい。

midiファイルを再生するアプリはTiMidityというのがよさそう。

timidityとSoundFontをインストール
```
$ sudo apt install timidity freepats fluid-soundfont-gm fluid-soundfont-gs
```
参考
- [FrontPage - KemaSoft](https://kemasoft.net/index.php#ke8617b0)

適当なmidiファイルを流し込む
```
$ cat sample.mid | timidity -
```
鳴った。

あとはもう一段何かをかませてあげれば目的が達成できる
```
$ cat sample.mml | nanika | timidity -
```
こんなイメージ

何かの参考になりそうなのは、このあたりかな・・
- [tr-takatsuka/rlib-MML: Music Macro Language Compiler](https://github.com/tr-takatsuka/rlib-MML)
- [mohayonao/mml-emitter: MML(Music Macro Language) event emitter for Web Audio API.](https://github.com/mohayonao/mml-emitter)
- [atsushieno/mugene-ng: Music Macro Language to MIDI 1.0 / 2.0 compiler](https://github.com/atsushieno/mugene-ng)
- [brnomade/MML_Interpreter: a Music Macro Language (MML) interpreter written in Python](https://github.com/brnomade/MML_Interpreter)
- [billletson/webaudio_mml: Implementation of Music Macro Language, played with the webaudio api](https://github.com/billletson/webaudio_mml)
- [mariomac/mmlmml: Toy Music Macro Language inspired in old 8-bit computers](https://github.com/mariomac/mmlmml)
- [myokoym/mml2wav: MML (Music Macro Language) to WAV audio converter by pure Ruby.](https://github.com/myokoym/mml2wav)
- [alexras/mml-tracker: An aborted attempt at a general-purpose tracker for Music Macro Language](https://github.com/alexras/mml-tracker)
- [ea909/mml.cpp: An MML (Music Macro Language) player that produces anti-aliased (bandlimited) output as wav files. Supports direct playback on Windows too.](https://github.com/ea909/mml.cpp)
- [zhidao/zmmlc: MML compiler](https://github.com/zhidao/zmmlc)
- [runvnc/music1: A simple way to play with MML (Music Macro Language). Enter MML in text area and press play button.](https://github.com/runvnc/music1)

というか、とりあえずMMLで遊びたいという欲求を満たすだけなら、上のリストの一番下をcloneしてきて`npx http-server`してlocalhost:8080開けばブラウザでできるし。
