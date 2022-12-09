---
title: "Codespacesの制限"
date: "2022-12-09"
tags: ["GitHub"]

---

GitpodからVS Codeに作業環境を引っ越して、docker-composeでコンテナ立てて動かせるようにしてみた。

が、airとかnextjsのホットリロードが効かない。
Windowsだとダメらしい。WSLで起動しても変わらず。

じゃあGitpodがPWAならある程度使い勝手が良いのでは？と思ったがGitpodはPWAに対応していなかった。

GitHub CodespacesはPWA対応しているようなので、リポジトリをGitHubに移してCodespaceで起動・・・使用としたができない。

今月割り当てられていたストレージ容量を使いきっていたようで、[Codespaces](https://github.com/codespaces)で作成済みの環境を削除しても回復しなかった。

npmパッケージの脆弱性対応とか、ちょっとした作業をCodespacesでやってたけど、終わったらすぐ消すようにしないと簡単に使い切ってしまうな。。
