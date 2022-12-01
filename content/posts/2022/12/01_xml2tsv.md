---
title: "KindleのXMLをTSVに変換する"
date: "2022-12-01"
tags: ["go"]

---

[umemak/kindle_xml_to_tsv](https://github.com/umemak/kindle_xml_to_tsv)作った。

ExcelだとXMLファイル読めるらしい（試してない）けど、Googleスプレッドシートだと読み込めなかったので、TSVに変換して読み込めた。

goの`encoding/xml`使って、割と簡単に書けたけど、AuthorsとPublishersが配列になっているところ、structを作って配列にしても最後のものしか読み込まれず、タグを`xml:"authors>author"`みたいにしたら解決できた。
