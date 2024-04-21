---
title: "ObsidianにRemotely Saveを導入した"
date: "2024-04-21"
tags: ["obsidian"]

---

[GitHub - remotely-save/remotely-save: Yet another unofficial Obsidian plugin allowing users to synchronize notes between local device and the cloud service. Supports S3, Dropbox, OneDrive, webdav.](https://github.com/remotely-save/remotely-save)

バックアップ先は[Cloudflare R2](https://www.cloudflare.com/ja-jp/developer-platform/r2/)を選択。
最近、Cloudflare気になっていたので良い機会。

設定手順も[remotely-save/docs/remote_services/s3_cloudflare_r2/README.md](https://github.com/remotely-save/remotely-save/blob/master/docs/remote_services/s3_cloudflare_r2/README.md)の通りで問題なかった。

ただ、E2E encryptionを設定したら、iPhone8やiPad air4には重すぎたようで同期が完了しないことがしばしば。
暗号化しなければ常識的な時間で同期できる。

あと使わなくなったバケットの削除をするのに、中身もまとめて削除するオプションがないのが不便といえば不便。
