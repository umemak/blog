---
title: "args"
date: "2022-01-30"

---

昨日のgo runとgo testで挙動が違うのは、os.argsのインデックスが間違っていただけだった・・

os.args[0] はコンパイルしたバイナリで、欲しかったものはos.args[1] でとれた。

なんか初歩的なところで時間溶かした。。