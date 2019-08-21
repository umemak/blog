---
title: nokogiri gem のアップデート
date: 2019-08-21
tags: [ "ruby", "docker" ]
---

* Githubから脆弱性の通知が来たので、`1.10.4`以上にバージョンアップ対応する。
* 作業環境はC223NAのdocker。

```
$ docker run -it -v `pwd`:/tmp ruby bash
# cd /tmp
# bundle update nokogiri
# bundle list nokogiri
/usr/local/bundle/gems/nokogiri-1.10.4
```
