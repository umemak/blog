---
title: "MLTファイルを作る3"
date: "2022-08-22"
tags: []

---

Shotcutでマーカーをchainの開始に合わせて配置したいと思って、mltにマーカーの記述を追加してみた。

Shotcutで開くと、なんかずれてる。

そもそも、mltファイルでは時間をミリ秒表記でやってるのに、アプリではフレーム単位？0～29で扱われているので、なんかその辺の誤差とかなのかなーとか、管理してる時間軸が違うのかなーとか。

あと、chainのoutを次のinと同じにするとズレが大きくなってる気もする。

ファイル上同じ文字列設定してるのに、読み込ませたらずれてしまうのはちょっと対処が大変そう。

