# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## プロジェクト概要
このリポジトリは、Hugo静的サイトジェネレーターを使用した日本語技術ブログです。GitHub Pagesでホスティングされ、Azure Pipelinesによる自動デプロイメントが設定されています。

## 開発コマンド
- **開発サーバー起動**: `hugo server`（ローカル開発時）
- **ビルド**: `hugo`（静的サイト生成）
- **新記事作成**: `hugo new posts/YYYY/MM/DD_title.md`
- **テーマ更新**: テーマディレクトリでの手動更新が必要

## コードベース構造
- **content/posts/**: ブログ記事（年/月のディレクトリ構造）
- **themes/**: Hugoテーマ（inkblotty、github-style）
- **static/admin/**: Netlify CMS管理画面
- **config.toml**: Hugo設定ファイル
- **azure-pipelines.yml**: CI/CDパイプライン設定

## 記事作成パターン
新しいブログ記事は以下の形式に従います：
- パス: `content/posts/YYYY/MM/DD_title.md`
- Front Matter必須項目: title、date、tags
- Markdownフォーマット
- 日本語コンテンツ

## デプロイメント
- masterブランチへのプッシュで自動デプロイ
- Azure PipelinesがHugo Extended v0.57.2を使用してビルド
- umemak.github.ioリポジトリへ自動プッシュ
- 最終的にGitHub Pagesで公開

## 設定情報
- ベースURL: https://umemak.github.io/blog
- 言語: 日本語（ja-jp）
- パーマリンク形式: /:slug/
- Google Analytics: UA-151652940-1
- Algolia検索機能統合
- Creative Commons BY-NC 4.0ライセンス

## テーマシステム
inkblottyテーマをメインで使用。WordPressのInkblotテーマをHugoに移植したもので、レスポンシブデザインと豊富なカスタマイズオプションを提供。