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

typographyのテーマをgithubに変更する
```
$ yarn add typography typography-theme-github
```
`src/utils/typography.js`を修正
```
$ git diff src/utils/typography.js
diff --git a/src/utils/typography.js b/src/utils/typography.js
index bc6b416..a493fef 100644
--- a/src/utils/typography.js
+++ b/src/utils/typography.js
@@ -1,17 +1,19 @@
 import Typography from 'typography'
-import Wordpress2016 from 'typography-theme-wordpress-2016'
+// import Wordpress2016 from 'typography-theme-wordpress-2016'
+import githubTheme from 'typography-theme-github'
 
-Wordpress2016.overrideThemeStyles = () => {
-  return {
-    'a.gatsby-resp-image-link': {
-      boxShadow: `none`,
-    },
-  }
-}
+// Wordpress2016.overrideThemeStyles = () => {
+//   return {
+//     'a.gatsby-resp-image-link': {
+//       boxShadow: `none`,
+//     },
+//   }
+// }
 
-delete Wordpress2016.googleFonts
+// delete Wordpress2016.googleFonts
 
-const typography = new Typography(Wordpress2016)
+// const typography = new Typography(Wordpress2016)
+const typography = new Typography(githubTheme)
 
 // Hot reload typography in development.
 if (process.env.NODE_ENV !== `production`) {
 ```
 
デフォルトだと長い行がコードブロックの枠を突き抜けるのでなんとかする。
 https://qiita.com/gipcompany/items/c878b6b757cadf2adb1d
 こちらを参考にパッケージの追加と、`gatsby-browser.js`と`gatsby-config.js`を編集する。
 ```
 $ yarn add gatsby-transformer-remark gatsby-remark-prismjs prismjs
 ```
 
