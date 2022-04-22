---
title: "HugoにAlgoliaを導入してみる"
date: "2022-04-22"
tags: ["hugo", "algolia"]

---

[Hugo + Algolia + Instantsearch.jsで静的サイトに全文検索を導入 - OTTANXYZ](https://ottan.xyz/posts/2021/07/947231059/)を見ながらやってみた。

とりあえずローカルでできることを確認してから、GitHub Actionsに組み込もうかと。

で、上記サイトは設定ファイルがYAMLだったのでTOMLで書くところで躓いた。
```toml
[outputFormats.Algolia]
  baseName = "algolia"
  isPlainText = true
  mediaType = "application/json"
  notAlternative = true
```
これで動いた。

```sh
$ sudo apt install npm
$ npm install -D atomic-algolia
$ touch .env
$ hugo --gc --minify --cleanDestinationDir
：
略
：
                   | JA   
-------------------+------
  Pages            | 441  
  Paginator pages  |  45  
  Non-page files   |  46  
  Static files     |   4  
  Processed images |   0  
  Aliases          |  83  
  Sitemaps         |   1  
  Cleaned          |   0  

Total in 394 ms

$ npx atomic-algolia
[Algolia] Adding 274 hits to blog
[Algolia] Updating 0 hits to blog
[Algolia] Removing 0 hits from blog
[Algolia] 0 hits unchanged in blog
：
略
：
```
できたっぽい。

Algoliaのサイトでもインデックスが登録されていることが確認できたので、ここまでの変更をPUSH。

・・・searchページが作成されていない。

うーん、もともと検索非対応のテーマだから仕方ないけど、深堀するの面倒だな。。
