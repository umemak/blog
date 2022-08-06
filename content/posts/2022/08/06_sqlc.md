---
title: "sqlcのエラー"
date: "2022-08-06"
tags: ["sqlc"]

---

```sql
-- name: ListEventUsers :many
SELECT eu.id, eu.eventid, eu.userid, eu.`status`, u.name
FROM (
    SELECT id, eventid, userid, `status`,
    row_number() OVER (PARTITION BY eventid, userid ORDER BY id DESC) AS num
    FROM eventUser
) eu, user u
WHERE eu.eventid = ?
  AND eu.num = 1
  AND eu.userid = u.id
ORDER BY eu.id;
```
これが
```sh
$ sqlc generate
# package sqlc
db/query.sql:14:1: table alias "eu" does not exist
```

adminerで実行したらちゃんと思った結果得られるのに。

[Table alias not working · Issue #1385 · kyleconroy/sqlc](https://github.com/kyleconroy/sqlc/issues/1385)のissueだとv1.10.0だと使えていたっぽい。

```sh
$ sqlc version
v1.14.0
$ go install github.com/kyleconroy/sqlc/cmd/sqlc@v1.10.0
$ sqlc version
v1.10.0
```

エラー消えて生成できるようになった。

たしかに1.11.0の[Releases](https://github.com/kyleconroy/sqlc/releases/tag/v1.11.0)に[fix(compiler): Validate table alias references by timstudd · Pull Request #1283 · kyleconroy/sqlc](https://github.com/kyleconroy/sqlc/pull/1283)がある。
