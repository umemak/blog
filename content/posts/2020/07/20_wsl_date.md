---
title: "WSLの時計を合わせる"
date: "2020-07-20"
tags: ["wsl"]
---

`apt update`したときにエラーになった場合の解決策のひとつ。
WSL側の時計が大幅にずれているパターン。

https://github.com/microsoft/WSL/issues/4245 を参考に。

```
# hwclock -s
```
