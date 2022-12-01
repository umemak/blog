---
title: "KindleのXMLをTSVに変換する"
date: "2022-12-01"
tags: ["go"]

---

[umemak/kindle_xml_to_tsv](https://github.com/umemak/kindle_xml_to_tsv)作った。

ExcelだとXMLファイル読めるらしい（試してない）けど、Googleスプレッドシートだと読み込めなかったので、TSVに変換して読み込めた。

goの`encoding/xml`使って、割と簡単に書けたけど、AuthorsとPublishersが配列になっているところ、structを作って配列にしても最後のものしか読み込まれず、タグを`xml:"authors>author"`みたいにしたら解決できた。

- [go - GolangでXMLの配列をパースしたい - スタック・オーバーフロー](https://ja.stackoverflow.com/questions/73021/golang%E3%81%A7xml%E3%81%AE%E9%85%8D%E5%88%97%E3%82%92%E3%83%91%E3%83%BC%E3%82%B9%E3%81%97%E3%81%9F%E3%81%84)
