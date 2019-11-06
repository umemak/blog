---
title: "Chromebookで画像編集"
date: "2019-11-06"
tags: ["chromebook"]
---

イベントの写真をブログに載せるのに、スマホのそのままだとサイズでかすぎるし、トリミングやリサイズもしたいときにどうすれば良いのか定まっていなかった。

とりあえずこれで行けそうな方法が見つかったのでメモ。

* やりたいこと
  - 画像のリサイズ、トリミング
  - Googleフォトにアップした画像を選択したい
  - 編集した画像はGithubにアップロードする
* 試したこと
  - ブラウザ版のGoogleフォト
    - トリミングはできるけど、リサイズができない
    - Githubのファイルアップロードするにはローカルにダウンロードする必要がある
  - 画像編集系のアプリ
    - Googleフォトの画像が直接開けない

* インストールしたアプリ
  - Googleフォト
    - https://play.google.com/store/apps/details?id=com.google.android.apps.photos&hl=ja
  - Photo Editor
    - https://play.google.com/store/apps/details?id=com.iudesk.android.photo.editor&hl=ja

ポイントは、Googleフォトのアプリ版を使うこと。

アプリ版だと、画像を開いたときにメニューから「編集用アプリ」が選択できる。
{{< figure src="../IMG_20191106_154759.jpg" title="" class="center" width="640" >}}

編集用アプリでPhoto Editorを選択すると、Photo Editorで画像が開けて編集できる。

編集後の画像はギャラリーに保存して、GithubにアップロードすればOK。

