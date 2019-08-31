---
title: JAWS-UG コンテナ支部 #15
date: 2019-08-29
tags: [ "aws", "container" ]
---

https://jawsug-container.connpass.com/event/143245/

## AWS コンテナサービスアップデート	トリ / Amazon Web Services Japan
* コンテナロードマップは what’s new に載ってない
* トランキングENIと通常のENIの違いは「ほとんど」ない
* EKS 名称変更が一番シェアされたツイート

## mazon ECSの開発環境を動的に管理するツールを作ってみました	プログラミングヤクザ / サイバーエージェント
* devxx環境の自動化
* 作るのに時間がかかるALBを共有化する
* PRと環境が対になる
  - create PR すると create ENV
  - close PR すると delete ENV
* dev00 は reference として使う
* github.com/baikonur-oss/docs で公開しました

## Fargate運用物語 ～ 本当にコンテナで幸せになりますか？ ～	曽根 壮大 / オミカレ
* EC2で困ってないならEC2で良い
* 冪等性を担保するAnsibleは難しい
　- 頻繁に変更があるならコンテナのほうが向いている
* サイドカー増やしたくなったらEC2でいいんじゃないか
* 解決したい問題のスコープ大事

## How Fast can your Fargate Scale?	Pahud Hsieh / Amazon Web Services
* スケールアップの検知を早くする（１〜３分→10秒以下）
* StepFunctionでstausをcorrectする（3秒ごと）

