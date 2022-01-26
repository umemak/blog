---
title: "マークダウンでMMLを書く"
date: "2022-01-26"

---

とりあえずリポジトリを作成して、VS CodeのDev Containerで開発できるようにした。

timidityはコンテナ内で実行しても出力デバイスが見つからないとかで動かなかった。

SMFの仕様は、Wikipedia見ても具体的にどうなのって感じで、脚注のリンク先も公式以外は消えてしまっていた。
エンディアンとか久しぶりに見た。
- [スタンダードMIDIファイル - Wikipedia](https://ja.wikipedia.org/wiki/%E3%82%B9%E3%82%BF%E3%83%B3%E3%83%80%E3%83%BC%E3%83%89MIDI%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB)

公式ページは仕様書のダウンロードにメンバー登録が必要っぽい。そこまで本格的にやるつもりは今のところないんだけど。

ググって出てきたこのページが参考になりそう。
- [Welcome to yyagi's web site. - SMF (Standard MIDI Files) の構造](https://sites.google.com/site/yyagisite/material/smfspec)
- [SMF ( Standard MIDI File ) Format1 のバイナリを読んでみた - ハトネコエ Web がくしゅうちょう](https://nekonenene.hatenablog.com/entry/2017/02/26/001351)
- [SMF(Standard MIDI File)フォーマット解説 | 技術的読み物 | FISH&BREAD](http://maruyama.breadfish.jp/tech/smf/)
