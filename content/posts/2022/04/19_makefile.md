---
title: "Makefile入門"
date: "2022-04-19"
tags: ["Makefile"]

---

普段使っていないわけではないけれど、GitHub Actionsで動かしたときに変数を変えたくて、ifで条件分ければ行けると思ったんだけど、うまくいかない。

```
VAR1 = "abc"
if [ "$(CI)" = "true" ]; then \
    VAR1 += "def"; \
fi
```

やりたいことはこんな感じなんだけど。
