---
title: "Goのinterfaceを学ぶ"
date: "2020-11-28"
tags: ["go"]
---

* golintの`exported %s %s returns unexported type %s, which can be annoying to use`を解消したい。
* interfaceを定義して回避するのが一般的？らしい。
* structが入れ子になっていて、内側のstructにメソッドが定義されていると、`cannot call pointer method`となり呼べない。
  * https://play.golang.org/p/yvWspYJnYSv
* pointerを返してあげれば良い。
  * https://play.golang.org/p/l_l4tMAD-Bd
