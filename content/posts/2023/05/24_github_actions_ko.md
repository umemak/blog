---
title: "GitHub Actionsでコンテナイメージを登録する"
date: "2023-05-24"
tags: ["GitHub", "ko", "go"]

---

[ko-build/setup-ko](https://github.com/ko-build/setup-ko) を使ったら簡単にできた。

<https://github.com/umemak/kindle_xml_to_tsv/blob/main/.github/workflows/ko.yml>で<https://github.com/umemak/kindle_xml_to_tsv/pkgs/container/kindle_xml_to_tsv%2Fkindle_xml_to_tsv-f222ca7f0849cd5cfa2ae78a69f0ff9a>こう。

最初実行したときに権限のエラーが出て、[GitHub Action で GHCR へのコンテナー イメージの Push が成功しない (permission_denied: write_package) - yukirii blog](https://blog.yukirii.dev/github-action-ghcr-push-error/)を参考に`Write`にして再実行したらエラー解消した。

ただ、最初の権限が`Admin`だったし、エラー出つつも物はアップロードされていたので謎。
