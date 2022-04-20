---
title: "Makefile入門"
date: "2022-04-20"
tags: ["Makefile"]

---

昨日の件、

```
VAR1 = "abc"
if [ "$(CI)" = "true" ]; then \
    VAR1 += "def"; \
fi
```

ではなく

```
VAR1 = "abc"
ifeq ($(CI),true)
    VAR1 += "def"
endif
```

で良かった。
ひとつ賢くなった。
