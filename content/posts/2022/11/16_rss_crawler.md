---
title: "RSSクローラー"
date: "2022-11-16"
tags: ["RSS"]

---

RSSリーダーは[Inoreader](https://www.inoreader.com/)をProプランで使っているのだけれど、そろそろ年払いの更新時期で、最近ちょっと下がったとはいえまだドルが高いので思案中。

そもそもProプランにしてるのは、ルールとフィルターが使いたいからで、それさえ自前で実現できれば、広告付きFreeプランでも問題ない（はず）。

ということでRSSクローラーを作ってみようかと。

その前にちょっと検索してみた結果をメモ

- [minhhungit/github-action-rss-crawler: Rss 100% auto crawling using Github Action](https://github.com/minhhungit/github-action-rss-crawler)
- [今更ながらGithub Actionsを用いてRSSフィードを自動取得・メール送信を実現する - Qiita](https://qiita.com/cacaoMath/items/2dfd6edc51e14cf9054b)
- [企業のテックブログの更新をまとめたRSSフィードを作りました！（GitHub Actions） - Qiita](https://qiita.com/yamadashy/items/0130e3e569b0832bc51f)
- [簡単すぎる！GitHubを自分だけのRSSリーダーに変える「osmos:feed」を使ってみた！ - paiza開発日誌](https://paiza.hatenablog.com/entry/2021/07/07/150000)
- [【Node.js】Qiita/Zennの投稿をGitHubのProfileに自動反映する。（半分ポエム）](https://zenn.dev/kinkinbeer135ml/articles/968c7f8a5f0767)
    - [note の RSS でクライアントから記事一覧を取得する方法【Cloud Functions for Firebase】 - to-R Media](https://www.to-r.net/media/note-rss/)
