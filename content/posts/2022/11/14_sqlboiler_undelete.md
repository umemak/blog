---
title: "SQLBoilerで論理削除の復旧"
date: "2022-11-14"
tags: ["go"]

---

SQLBoilerはDeleteするときに論理削除が使える。

詳細は[【Go】sqlboilerで論理削除を実装する | ISSUE](https://i-ssue.com/topics/b28d30d1-7bb4-4a6d-b669-f818ba9e7de3)が詳しい。

論理削除のときは`deleted_at`カラムがセットされる。

で、そのとき`updated_at`は更新されない。

論理削除した行を元に戻したいとき、`deleted_at`に`null.Time{}`をセットしてupdateすれば元通りになるかというと、`updated_at`が更新されてしまって完全に元通りとは言えない状態。

どうするか。
[volatiletech/sqlboiler: Generate a Go ORM tailored to your database schema.](https://github.com/volatiletech/sqlboiler#skipping-automatic-timestamps)にあるように、contextで`boil.SkipTimestamps`を使う。

つまり`model.Update(boil.SkipTimestamps(context.Background()), db , boil.Infer())`こんな感じ。
