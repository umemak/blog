---
title: "GatsbyJSでBlogを構築する"
date: "2020-03-27"
tags: ["gatsbyjs"]
---

GatsbyJSでblogを構築します。

環境はGitHubに空のリポジトリ（blog-gatsby）を作成して、Gitpodで開いたところから。

starterとして[gatsby-starter-blog-mdx](https://www.gatsbyjs.org/starters/hagnerd/gatsby-starter-blog-mdx/)を採用。

すでに`.git`ディレクトリが存在するとエラーになるので、一旦リネームしてセットアップする。
途中でパッケージマネージャーを`npm`と`yarn`どちらを使うか聞かれるので、`yarn`を選択。

```
$ cd ..
$ mv blog-gatsby{,.bk}
$ npx gatsby new blog-gatsby https://github.com/hagnerd/gatsby-starter-blog-mdx
```

差分を戻す
```
$ cp blog-gatsby.bk/.git/config blog-gatsby/.git/config
$ cp blog-gatsby.bk/.git/hooks/pre-commit.sample blog-gatsby/.git/hooks/pre-commit.sample
$ cp blog-gatsby.bk/.git/hooks/update.sample blog-gatsby/.git/hooks/update.sample
```

ここまでコミット
```
$ rm -rf blog-gatsby.bk
$ cd blog-gatsby
$ git push origin HEAD
```

表示確認
```
$ yarn dev
```

