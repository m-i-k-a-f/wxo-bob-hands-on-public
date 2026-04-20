# watsonx Orchestrate セットアップガイド

IBM Bob と watsonx Orchestrate を使った開発環境のセットアップガイドです。

## 📚 概要

このリポジトリは、ブラウザ閲覧型のセットアップガイドです。
IBM Bob、watsonx Orchestrate、MCP、ContentIQ の環境構築手順を提供します。

### 📖 ガイド構成

ガイドは以下の構成になっています：

1. **[環境構築ガイド](setup/index.html)** - すべてのセットアップ手順を網羅
2. **個別セットアップページ** - 各コンポーネントの詳細手順

## 🎯 学べること

- IBM Bob のセットアップと基本設定
- watsonx Orchestrate の利用開始と ADK の導入
- MCP (Model Context Protocol) の設定方法
- IBM ContentIQ の環境構築

## 🚀 クイックスタート

### 前提条件

- Visual Studio Code
- IBM Bob を利用できる環境
- IBM Cloud アカウント
- watsonx Orchestrate を利用できる環境
- ブラウザ
- ローカルで静的ファイルを配信できる環境  
  例: Python の簡易HTTPサーバー、または Node.js の [`http-server`](https://www.npmjs.com/package/http-server)

### ガイドの開き方

1. このリポジトリをローカルに配置
2. 任意の方法でローカルサーバーを起動
3. ブラウザで [`setup/index.html`](setup/index.html) を開く

#### 例: Python を使う場合

```bash
python -m http.server 8010
```

#### 例: Node.js を使う場合

```bash
npx http-server -p 8010
```

起動後、以下にアクセスします。

```text
http://localhost:8010
```

## 📖 ガイド構成

### 環境構築ガイド

**統合ガイド:** [setup/index.html](setup/index.html)
- すべてのセットアップ手順を1つのページで確認
- ステップバイステップの説明
- トラブルシューティング情報
- 所要時間の目安

**個別セットアップページ:**
- [Bob セットアップ](setup/bob-setup.html)
- [watsonx Orchestrate セットアップ](setup/orchestrate-setup.html)
- [MCP セットアップ](setup/mcp-setup.html)
- [ContentIQ セットアップ](setup/contentiq-setup.html)

## 🛠️ 技術要素

- IBM Bob
- watsonx Orchestrate
- watsonx Orchestrate ADK
- MCP (Model Context Protocol)
- IBM ContentIQ
- Python
- HTML / CSS / JavaScript

## 📁 ディレクトリ構成

```text
wxo-bob-hands-on-public/
├── README.md
└── setup/
    ├── index.html
    ├── bob-setup.html
    ├── orchestrate-setup.html
    ├── mcp-setup.html
    └── contentiq-setup.html
```

## 🧪 セットアップの進め方

### 推奨される手順

1. **[環境構築ガイド](setup/index.html)** を開く
2. 以下の順序でセットアップを実施：
   - Bob のセットアップ
   - watsonx Orchestrate と ADK のセットアップ
   - MCP の設定
   - ContentIQ の準備

### 特定のステップのみ確認したい方

[setup/](setup/) 内の個別ページを直接参照してください。

## 🔗 参考リンク

- [watsonx Orchestrate ADK インストールガイド](https://developer.watson-orchestrate.ibm.com/getting_started/installing)
- [MCP in Bob](https://bob.ibm.com/docs/ide/configuration/mcp/mcp-in-bob)
- [Model Context Protocol 公式サイト](https://modelcontextprotocol.io/)
- [IBM Cloud](https://cloud.ibm.com/)

## 🎓 ガイドの使い分け

### 環境構築ガイド ([setup/index.html](setup/index.html))

**こんな時に使用:**
- 初めて環境をセットアップする
- すべてのセットアップ手順を順番に確認したい
- セットアップ全体の所要時間を知りたい
- トラブルシューティング情報をまとめて確認したい

### 個別セットアップページ

**こんな時に使用:**
- 特定のセットアップステップのみを確認したい
- 詳細な手順を確認したい
- 特定のコンポーネントの設定を見直したい

## 📝 補足

このセットアップガイドは、2つの階層で構成されています：

1. **統合ガイド** ([setup/index.html](setup/index.html)) - セットアップ全体の流れ
2. **個別ページ** - 各コンポーネントの詳細手順

この構造により、初心者は統合ガイドで全体の流れを把握しながらセットアップでき、経験者は個別ページで必要な情報に素早くアクセスできます。

---

最終更新: 2026-04-17