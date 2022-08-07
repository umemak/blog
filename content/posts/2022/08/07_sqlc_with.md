---
title: "sqlcのエラー2"
date: "2022-08-07"
tags: ["sqlc"]

---

sqlc@v1.10.0だと、
```sql
-- name: ListCommentsTree :many
WITH RECURSIVE r AS (
    SELECT * FROM comments WHERE comments.id = ?
    UNION ALL
    SELECT comments.* FROM comments, r WHERE comments.parent_id = r.id
)
SELECT * FROM r;
```
これが
```sh
$ sqlc generate
# package sqlc
db/query.sql:35:5: syntax error near "WITH RECURSIVE r AS ("
```
こう。

sqlc@latestにするとこれは解消するけれど、昨日のtable aliasエラーが。。

うーん。
