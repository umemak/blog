---
author: "umemak"
date: 2019-08-21
title: Azure DevOpsでCI
# tags: [ "Azure", "DevOps", "hugo" ]
---

* Hugoの実行とPUSHをやってもらう
* https://blog.kaikeru.com/post/20181228-freestaticsite/ を参考に設定。
* [CIのスキップ](https://docs.microsoft.com/ja-jp/azure/devops/pipelines/build/triggers?view=tfs-2018&tabs=yaml#ci-triggers)を念の為追加
* [variableの設定](https://docs.microsoft.com/en-us/azure/devops/pipelines/process/variables?view=azure-devops&tabs=yaml%2Cbatch#secret-variables)がわかりにくかった。
  - ちゃんと読めば書いてある。
  - Pipeline編集画面の右上から。
  - AWS Secrets Manager的なサービスがあるのかと探し回ってしまった。。
