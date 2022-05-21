---
title: "Flutter+Kuzzle"
date: "2022-05-21"
tags: ["flutter", "Kuzzle"]

---

KuzzleのFlutterチュートリアル的なものをやってみた。

[Flutter | Kuzzle Documentation](https://docs.kuzzle.io/sdk/dart/3/getting-started/flutter/)

Dart Null Safety v3.x を選択しても、中身はv2と同じようだ。
pubspec.yamlのSDKバージョン指定まで同じなので、v2系がインストールされてしまって`flutter build web`実行したときにコンパイルエラーになる。
`kuzzle: ^3.0.2`に編集したらコンパイル通った。

あと、サンプルのコードが断片的で、完成品が示されていないので（とくに chat.dart）理解が進みにくいと思った。

