# watsonx Orchestrate/IBM Bob/ContentIQ ハンズオンガイド

このガイドでは、各製品のセットアップ手順とハンズオンラボを提供します。

## 📋 目次

- [このガイドについて](#このガイドについて)
- [セットアップ手順](#セットアップ手順)
  - [1. IBM Bobのセットアップ](#1-ibm-bobのセットアップ)
  - [2. watsonx Orchestrateのセットアップ](#2-watsonx-orchestrateのセットアップ)
  - [3. MCPサーバー接続のセットアップ](#3-mcpサーバー接続のセットアップ)
  - [4. ContentIQのセットアップ](#4-contentiqのセットアップ)
- [ハンズオンラボ](#ハンズオンラボ)
  - [Lab 1: IT Support Agentの実装とデプロイ](#lab-1-it-support-agentの実装とデプロイ)
  - [Lab 2: ContentIQでRAG構築](#lab-2-contentiqでrag構築)
  - [参考: ITサポートエージェント仕様書](#参考-itサポートエージェント仕様書)
- [参考リンク](#参考リンク)

---

## このガイドについて

### 環境構築の目的

このガイドでは、watsonx Orchestrateを使ったAIエージェント開発とContentIQでのRAG実装に必要な環境を構築します。

### セットアップする環境

- ✅ IBM Bob（AI開発アシスタント）
- ✅ watsonx Orchestrate（AIエージェントプラットフォーム）
- ✅ MCP（Model Context Protocol）サーバー接続
- ✅ ContentIQ（RAGシステム用）

## セットアップ手順

### 1. IBM Bobのセットアップ

IBM Bobは、AI開発アシスタントです。

📖 **[詳細ガイドを見る →](setup_md/01_bob-setup.md)**

---

### 2. watsonx Orchestrateのセットアップ

watsonx Orchestrateの環境を準備し、ADK（Agent Development Kit）をインストールします。

📖 **[詳細ガイドを見る →](setup_md/02_orchestrate-setup.md)**

---

### 3. MCPサーバー接続のセットアップ

Model Context Protocol (MCP) を使ってBobとwatsonx Orchestrateを統合します。

📖 **[詳細ガイドを見る →](setup_md/mcp-setup.md)**

---

### 4. ContentIQのセットアップ

ContentIQを使ってRAGシステムを構築します。

📖 **[詳細ガイドを見る →](setup_md/04_contentiq-setup.md)**

---

## ハンズオンラボ

環境構築が完了したら、以下のハンズオンラボで実践的なスキルを習得できます。

### Lab 1: IT Support Agentの実装とデプロイ

Bobを使ってエージェントを実装し、watsonx Orchestrateにデプロイします。

📖 **[Lab 1を始める →](labs/lab1-basic-agent.md)**

---

### Lab 2: ContentIQでRAG構築

watsonx Orchestrate公式ドキュメントを使ったRAGシステムを構築します。

📖 **[Lab 2を始める →](labs/lab2-contentiq.md)**

---

### 参考: ITサポートエージェント仕様書

Lab 1で使用するITサポートエージェントの仕様書です。

📖 **[仕様書を見る →](labs/WxO_it_support_draft_agent_spec_jp.md)**

---

## 参考リンク

- [watsonx Orchestrate ADK インストールガイド](https://developer.watson-orchestrate.ibm.com/getting_started/installing)
- [MCP in Bob](https://bob.ibm.com/docs/ide/configuration/mcp/mcp-in-bob)
- [Model Context Protocol 公式サイト](https://modelcontextprotocol.io/)
- [IBM Cloud](https://cloud.ibm.com/)
