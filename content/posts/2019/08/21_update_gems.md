---
title: ruby gem のアップデート
date: 2019-08-21
# tags: [ "ruby", "docker" ]
---

* Githubから脆弱性の通知が来たので、nokogiriを`1.10.4`以上に、actionviewを`5.1.6.2`以上にバージョンアップ対応する。
* 作業環境はC223NAのdocker。

```
$ docker run -it -v `pwd`:/usr/src/work ruby bash
# cd /usr/src/work
# bundle update nokogiri
# bundle list nokogiri
/usr/local/bundle/gems/nokogiri-1.10.4
```

* 最初nokogiriの通知しか出てなかったのに、更新してpushしたらもういっこうあるでってactionview出てきた。。
* actionview は、`bundle update actionview`では更新されず、`bundle update`で全部上げるようにしたら上がった。
