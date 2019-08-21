---
author: "umemak"
date: 2019-07-18
title: MacbookPro初期化
---

# MacbookPro初期化

Chromebook買ってからほとんど出番ないので売ってしまおうと。

その前にディスクの初期化・・・SSDの場合ってHDDと同じ方法でいいんだっけ？という話。

参考：
- [Mac を売却、譲渡、下取りに出す前にやっておくべきこと](https://support.apple.com/ja-jp/HT201065)
- [Mac のディスクを消去する方法](https://support.apple.com/ja-jp/HT208496)
- [Mac OS Xで、SSDのデータを安全に消去する方法](https://www.lifehacker.jp/2014/06/140601erase_solid_state.html)

結論としては、HDDと同じではない。消去のオプションがそもそも出てこない（何回書き込むとか選ぶやつ）。

手順は、起動時に`Command`+`R`でディスクユーティリティ起動して削除後OSの再インストールを実施。

で、再インステール後にコマンドラインで`sudo diskutil randomDisk 2 /dev/disk1`実行してもunmountできないとかエラー出てダメ。

何度かディスクユーティリティで削除＆OS再インストールしていたら、ネットワークからの復元的な英語のになって、インストールできるOSが・・・Mavericksっていつのやつだ。

今日のところはMAvericksインストールまでで時間切れ。
