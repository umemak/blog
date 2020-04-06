---
title: "NextJSとdotenvでハマった"
date: "2020-04-06"
tags: ["nextjs"]
---

reactでdotenv使うとき、起動モードごとに定義ファイルを変えられるように、`.env.development`にしていたので、同じようにやったら読み込まれない。

NextJSで使うときは、`.env`しか認識してくれないらしい。
環境ごとにファイル分けたい場合のやり方は、未調査。
