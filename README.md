# watsonx Orchestrate 環境構築ガイド

IBM Bob と watsonx Orchestrate の開発環境をセットアップします。

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

## セットアップ手順

### 1. IBM Bobのセットアップ

IBM Bobは、AI開発アシスタントです。

📖 **[詳細ガイドを見る →](setup_md/bob-setup.md)**

---

### 2. watsonx Orchestrateのセットアップ

watsonx Orchestrateの環境を準備し、ADK（Agent Development Kit）をインストールします。

📖 **[詳細ガイドを見る →](setup_md/orchestrate-setup.md)**

---

### 3. MCP統合のセットアップ

Model Context Protocol (MCP) を使ってBobとwatsonx Orchestrateを統合します。

📖 **[詳細ガイドを見る →](setup_md/mcp-setup.md)**

---

### 4. ContentIQのセットアップ

ContentIQを使ってRAGシステムを構築します。

📖 **[詳細ガイドを見る →](setup_md/contentiq-setup.md)**

---

## 参考リンク

- [watsonx Orchestrate ADK インストールガイド](https://developer.watson-orchestrate.ibm.com/getting_started/installing)
- [MCP in Bob](https://bob.ibm.com/docs/ide/configuration/mcp/mcp-in-bob)
- [Model Context Protocol 公式サイト](https://modelcontextprotocol.io/)
- [IBM Cloud](https://cloud.ibm.com/)

---

© 2026 IBM watsonx Orchestrate セットアップガイド