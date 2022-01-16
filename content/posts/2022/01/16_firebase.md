---
title: "続々・Firebase認証をvueで使う"
date: "2022-01-16"

---

エラーメッセージ`Uncaught TypeError: Cannot read properties of undefined (reading 'initializeApp')`でぐぐって出てきた
- [javascript - Uncaught TypeError: Cannot read property 'initializeApp' of undefined - Stack Overflow](https://stackoverflow.com/questions/59050195/uncaught-typeerror-cannot-read-property-initializeapp-of-undefined)

を参考にしたら、エラー解消して一歩進んだ。
上記回答にも書いてあるが、

- [Upgrade from version 8 to the modular Web SDK  |  Firebase Documentation](https://firebase.google.com/docs/web/modular-upgrade#about_the_upgrade_process)

ドキュメントに書いてある（以前自分も見つけてたやつだけど、ふむふむ互換パッケージが用意されてるのね、程度できちんと読んでなかった）。

公式ドキュメント読むの大事。
