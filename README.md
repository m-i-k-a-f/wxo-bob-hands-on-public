# watsonx Orchestrate 環境構築ガイド

IBM Bob と watsonx Orchestrate の開発環境をセットアップする

---

## 📋 目次

- [このガイドについて](#このガイドについて)
- [セットアップ手順](#セットアップ手順)
  - [1. IBM Bobのセットアップ](#1-ibm-bobのセットアップ)
  - [2. watsonx Orchestrateのセットアップ](#2-watsonx-orchestrateのセットアップ)
  - [3. MCP統合のセットアップ](#3-mcp統合のセットアップ)
  - [4. ContentIQのセットアップ](#4-contentiqのセットアップ)
- [参考リンク](#参考リンク)

---

## このガイドについて

### 環境構築の目的

このガイドでは、watsonx Orchestrateを使ったAIエージェント開発に必要な環境を構築します。

### セットアップする環境

- ✅ IBM Bob（AI開発アシスタント）
- ✅ watsonx Orchestrate（AIエージェントプラットフォーム）
- ✅ MCP（Model Context Protocol）統合
- ✅ ContentIQ（RAGシステム用）

### 前提条件

- Visual Studio Code がインストールされていること
- IBM Cloud アカウントを持っていること
- watsonx Orchestrate へのアクセス権があること
- 基本的なコマンドライン操作の知識

### 所要時間

⏱️ 約60〜90分

---

## セットアップ手順

### 1. IBM Bobのセットアップ

IBM Bobは、VS Code拡張機能として提供されるAI開発アシスタントです。

**セットアップ内容：**
- VS Code拡張機能のインストール
- IBM Cloudアカウントとの連携
- 基本設定の確認

📖 **[詳細ガイドを見る →](setup_md/bob-setup.md)**

---

### 2. watsonx Orchestrateのセットアップ

watsonx Orchestrateの環境を準備し、ADK（Agent Development Kit）をインストールします。

**セットアップ内容：**
- watsonx Orchestrateへのアクセス確認
- APIキーの取得
- ADKのインストール
- 接続テスト

📖 **[詳細ガイドを見る →](setup_md/orchestrate-setup.md)**

---

### 3. MCP統合のセットアップ

Model Context Protocol (MCP) を使ってBobとwatsonx Orchestrateを統合します。

**セットアップ内容：**
- MCP Serverのインストール
- Bob設定ファイルの編集
- 接続の確認
- 基本的な動作テスト

📖 **[詳細ガイドを見る →](setup_md/mcp-setup.md)**

---

### 4. ContentIQのセットアップ

Watson Discovery (ContentIQ) を使ってRAGシステムを構築します。

**セットアップ内容：**
- ContentIQインスタンスの作成
- APIキーの取得
- プロジェクトの作成
- 接続設定

📖 **[詳細ガイドを見る →](setup_md/contentiq-setup.md)**

---

## 参考リンク

- [watsonx Orchestrate ADK インストールガイド](https://developer.watson-orchestrate.ibm.com/getting_started/installing)
- [MCP in Bob](https://bob.ibm.com/docs/ide/configuration/mcp/mcp-in-bob)
- [Model Context Protocol 公式サイト](https://modelcontextprotocol.io/)
- [IBM Cloud](https://cloud.ibm.com/)

---

© 2026 IBM watsonx Orchestrate セットアップガイド