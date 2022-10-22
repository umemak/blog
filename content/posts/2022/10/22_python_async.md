---
title: "Pythonで非同期処理"
date: "2022-10-22"
tags: ["python"]

---

今の作りだと、翻訳や英語再生の間、待たされる気がするので、翻訳APIから先は非同期で実行できないか調べてみた。

- [【Python】同期処理をラッピングして非同期処理にする方法 – 株式会社シーポイントラボ ｜ 浜松のシステム・RTK-GNSS開発](https://cpoint-lab.co.jp/article/202208/23186/)
- [python - asyncioを使った簡単なプログラムでエラーがでる。 - スタック・オーバーフロー](https://ja.stackoverflow.com/questions/70119/asyncio%E3%82%92%E4%BD%BF%E3%81%A3%E3%81%9F%E7%B0%A1%E5%8D%98%E3%81%AA%E3%83%97%E3%83%AD%E3%82%B0%E3%83%A9%E3%83%A0%E3%81%A7%E3%82%A8%E3%83%A9%E3%83%BC%E3%81%8C%E3%81%A7%E3%82%8B)
- [python3 の async/awaitを理解する - Qiita](https://qiita.com/maueki/items/8f1e190681682ea11c98)
- [asyncioでPythonの非同期処理を書いてみる | DevelopersIO](https://dev.classmethod.jp/articles/python-asyncio/)

`asyncio`をimportして、関数定義に`async`つけて、メイン処理は`asyncio.run`で呼び出し、非同期処理を`await`で呼び出せばいけるっぽい。

やってみたところ、どうも思った動きをしていない気がする。
普通に待ってるっぽい。

うーん。
