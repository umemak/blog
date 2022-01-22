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
