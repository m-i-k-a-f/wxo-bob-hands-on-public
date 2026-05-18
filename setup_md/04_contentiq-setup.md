# ContentIQセットアップガイド

ContentIQの環境構築を行います。

---

## 📋 目次

- [ContentIQとは](#contentiqとは)
- [ContentIQの起動確認](#contentiqの起動確認)
- [管理者による設定](#管理者による設定)
- [セットアップ完了](#セットアップ完了)

---

## ContentIQとは

ContentIQは、symplistic.aiが提供する、RAG構築ソリューションです。

### 主な機能

- ✅ 自然言語による高度な検索
- ✅ ドキュメント理解とエンティティ抽出
- ✅ 多言語サポート

---
## インスタンスの作成ガイド

**URL:** [https://ibm.github.io/japan-technology/onboarding-docs/watsonx-orchestrate/01_instance/04_create_instance](https://ibm.github.io/japan-technology/onboarding-docs/watsonx-orchestrate/01_instance/04_create_instance)

watsonx OrchestrateをContentIQに置き換えて、インスタンスを作成します。

インスタンス作成が完了すると、以下のメールが届きます。

![ContentIQ Start](../images/ciqstart.png)


## ContentIQの起動確認

### 手順

1. ContentIQにアクセスします
   
   **URL:** [https://contentiq.symplistic.ai](https://contentiq.symplistic.ai)

2. 初めてログインする場合は、watsonx Orchestrateの認証情報(APIキーとURL)の入力を求められるので、控えたものを入力します

3. ContentIQのホーム画面が表示されたら、ログインが完了です

---

## 管理者による設定

### ユーザー追加手順

1. ContentIQのHomeから、「Administrative Setting」をクリックします

   ![ciq1](../images/ciq1.png)

2. 「Role Setting」では「Administrator」や「Member」など権限のレベルを設定できます

   ![ciq2](../images/ciq2.png)

3. 「Account Assignments」ではメンバーの追加や削除ができます。新規追加をするには、「Add New User」をクリックします

   ![ciq3](../images/ciq3.png)

4. メールアドレスを入力し、適切なRoleを割り当てて「invite User」をクリックします

   ![ciq4](../images/ciq4.png)

5. 追加したメンバーにはメールが届きます。24時間以内にActivateする必要があります

   ![ciq5](../images/ciq5.png)

### watsonx Orchestrateの設定

+ ①「Setting」をクリック、②「watsonx Orchestrate」をクリックします。watsonx Orchestrateのセットアップで控えた、資格情報(URL、APIキー)を入力します

   ![ciq6](../images/ciq6.png)
---


### セットアップした環境

- ✅ IBM Bob - AI開発アシスタント
- ✅ watsonx Orchestrate - AIエージェントプラットフォーム
- ✅ MCP統合 - BobとOrchestrateの連携
- ✅ ContentIQ - RAGシステム構築基盤

### 💡 次のステップ

これで、IBM BobとwatsonX Orchestrateを使ったAIエージェント開発の準備が整いました。実際のエージェント開発を始めることができます。

➡️ **[Lab 1: IT Support Agent の実装とデプロイ](../labs/lab1-it-support-agent.md)**

---

**ナビゲーション:**
- [← MCPセットアップ](mcp-setup.md)
- [← README に戻る](../README.md)

---

© 2026 IBM watsonx Orchestrate セットアップガイド