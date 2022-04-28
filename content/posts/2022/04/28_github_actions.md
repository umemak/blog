---
title: "GitHub Actionsのmatrix"
date: "2022-04-28"
tags: ["github"]

---

[GitHub Actionsのワークフロー構文 - GitHub Docs](https://docs.github.com/ja/actions/using-workflows/workflow-syntax-for-github-actions)

この`jobs.<job_id>.strategy.matrix`は、jobに含まれるstepsをmatrixの組み合わせでループ実行するという理解。

同じようなことを、step単位でやりたいときにうまい方法がないかなぁ、と。

```yaml
jobs:
  example:
    steps:
      - name: example begin
        run: echo "begin"
      - name: example A
        run: echo "A"
      - name: example B
        run: echo "B"
```

こんなイメージのフローがあったとして、beginは共通で一度だけ実行したくて、AとBは記述をまとめて省略したい、みたいな。

[Github Actionsで繰り返し(ループ)処理 | r blog](https://r-blog.org/github-actions-loop/)

runの中でfor使ってループはできるみたいだけど、
```yaml
jobs:
  example:
    steps:
      - name: example begin
        run: echo "begin"
      - name: examples
        run: |
          for x in A B; do
            echo x
          done
```
たぶんこれだとひとつのstepに全部入ってしまうので、やりたいこととは違う。

