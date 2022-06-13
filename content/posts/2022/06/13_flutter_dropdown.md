---
title: "FlutterのDropdownを使う"
date: "2022-06-13"
tags: ["Flutter"]

---

[DropdownButton class - material library - Dart API](https://api.flutter.dev/flutter/material/DropdownButton-class.html)のサンプルを持ってきて、サンプルではchildとvalueを同じ文字列にしてるのを別々に指定できるようにして、とりあえずループ使わないで配列直接指定にしてみたら、エラー。

```
Assertion failed:
file:///home/umemak/sdk/flutter/packages/flutter/lib/src/material/dropdown.dart:882:15
items == null || items.isEmpty || value == null ||
              items.where((DropdownMenuItem<T> item) {
                return item.value == value;
              }).length == 1
"There should be exactly one item with [DropdownButton]'s value: One. \nEither zero or 2 or more
[DropdownMenuItem]s were detected with the same value"
```

dropdownValueの初期値をサンプルからコピーしたまま直してなかった。。

あと画面レイアウトは最初に全部作り切ったほうが良いと思った。
書き方忘れて調べるの面倒。。
