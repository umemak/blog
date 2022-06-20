---
title: "Flutterでリロードしたときもログイン状態を維持する"
date: "2022-06-20"
tags: ["Flutter"]

---

毎回ログイン画面に遷移して面倒だなぁと思っていた件。

[FlutterWebでFirebaseAuthのcurrentUserがリロード時にnullになることに対しての対処法](https://zenn.dev/kboy/articles/4c398560a2518f)

同様に、runAppの前に
```dart
await FirebaseAuth.instance.userChanges().first;
```
を入れたら解消した。
