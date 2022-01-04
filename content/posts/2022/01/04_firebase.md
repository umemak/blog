---
title: "Firebaseでやってみる"
date: "2022-01-04"

---

Amplifyで挫折したお題を、Firebaseで作り比べてみる。

Firebaseでプロジェクトを作成、前回と同じリポジトリでCodespacesを起動。

「ウェブアプリへのFirebaseの追加」手順に沿ってインストール。

```
$ npm install firebase
```

src/main.js のAmplify関連で追加した部分を削除、Firebaseのコードをコピペ。

Hosting用にCLIをインストール。
```
$ npm install -g firebase-tools
```

Firestoreの初期化。テストモードで東京（asia-northeast1）を選択。

コマンドラインからもろもろインストール。
```
$ firebase login
$ firebase init
Firestore
Hosting
Storage
Emulators
```

テストデプロイ
```
$ firebase deploy
```

あっさり Deploy complete! と出るが、ブラウザで表示しても何も出ない（viewsとかまだAmplify前提なので当たり前）

