---
title: "keep2md"
date: "2022-12-29"
tags: ["obsidian"]

---

Google KeepのエクスポートしたJSONをマークダウンファイルに変換する部分は一応できた。

[umemak/keep2md](https://github.com/umemak/keep2md)

一応というのは、本文が`textContent`に出力されているものしか対応していないし、プラグインにもしていないから。

チェックボックスとか使うと別の項目名になるので、取れていない。

自分の用途だとこれでほぼ変換できたので、この先の実装を進めるかどうかはいったん保留。
