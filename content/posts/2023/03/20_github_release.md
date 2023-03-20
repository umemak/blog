---
title: "GitHubのReleaseをActionsで"
date: "2023-03-20"
tags: []

---

GoReleaserがモノリポだと課金が必要な件。

[umemak/release_test](https://github.com/umemak/release_test)でいろいろ試してみた。

クロスコンパイルや圧縮が不要なら[softprops/action-gh-release: 📦 GitHub Action for creating GitHub Releases](https://github.com/softprops/action-gh-release)を使うのが簡単で良さそう。

今回の調査で、[x-motemen/gobump: Bumps up Go program version](https://github.com/x-motemen/gobump)が便利だと思った。

