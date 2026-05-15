# watsonx Orchestrate MCP統合セットアップガイド（GA版対応）

このガイドでは、IBM Bobでwatsonx Orchestrate MCPサーバーを設定する方法を説明します。

---

## 📋 目次

- [MCPとは](#mcpとは)
- [前提条件](#前提条件)
- [インストール手順](#インストール手順)
  - [ステップ1: 前提条件の確認](#ステップ1-前提条件の確認)
  - [ステップ2: uvパッケージマネージャーのインストール](#ステップ2-uvパッケージマネージャーのインストール)
  - [ステップ3: MCP設定ファイルの作成](#ステップ3-mcp設定ファイルの作成)
  - [ステップ4: Bobでの接続](#ステップ4-bobでの接続)
  - [ステップ5: 動作確認](#ステップ5-動作確認)
- [トラブルシューティング](#トラブルシューティング)
- [参考リンク](#参考リンク)

---

## MCPとは

Model Context Protocol (MCP)は、AIモデルと外部ツール・システムを標準化された方法で接続するためのオープンプロトコルです。IBM BobはMCPをサポートしており、watsonx Orchestrateとシームレスに統合できます。

> 💡 **詳細情報:** MCPの詳細については、[公式ドキュメント](https://modelcontextprotocol.io/)を参照してください。

---

## 前提条件

以下のソフトウェアが必要です：

- **Python 3.11以上**: watsonx Orchestrate ADK MCPサーバーの実行に必要
- **uv**: Pythonパッケージマネージャー（推奨）
- **watsonx Orchestrate環境**: ADKの設定ファイル（`~/.orchestrate/config.yaml`）が必要

---

## インストール手順

### ステップ1: 前提条件の確認

#### 1.1 Pythonバージョンの確認

ターミナルで以下のコマンドを実行して、Python 3.11以上がインストールされているか確認します：

```bash
python --version
```

または

```bash
python3 --version
```

**期待される出力例:**
```
Python 3.11.0
```

> ⚠️ **注意:** Python 3.11未満の場合は、[公式ドキュメント](https://developer.watson-orchestrate.ibm.com/getting_started/installing)を参照してPythonをアップグレードしてください。

#### 1.2 watsonx Orchestrate ADK設定の確認

watsonx Orchestrate ADKの設定ファイルが存在するか確認します：

**Windows (コマンドプロンプト):**
一番上の階層で、以下のコマンドを実行します：
```cmd
dir Users\user1\.config\orchestrate\config.yaml
```

**期待される出力例（Windows コマンドプロンプト）:**
```
2026/01/15  10:30             1,234 config.yaml
               1 個のファイル               1,234 バイト
```

> ⚠️ **設定ファイルが存在しない場合:**
>
> 以下のコマンドでwatsonx Orchestrate ADKをセットアップしてください：
>
> ```bash
> # ADKのインストール
> pip install ibm-watsonx-orchestrate
>
> # 環境の設定（対話形式で設定を行います）
> orchestrate env setup
> ```
>
> 詳細は[watsonx Orchestrate ADKのセットアップガイド](https://developer.watson-orchestrate.ibm.com/getting_started/installing)を参照してください。

**設定ファイルの内容確認（オプション）:**

設定ファイルの内容を確認したい場合は、以下のコマンドを実行します：

**Windows (コマンドプロンプト):**
一番上の階層で、以下のコマンドを実行します：
```cmd
type Users\user1\.config\orchestrate\config.yaml
```

設定ファイルには、接続先のwatsonx Orchestrate環境の情報（URL、認証情報など）が含まれています。

---

### ステップ2: MCPサーバー実行環境のセットアップ

watsonx Orchestrate ADK MCPサーバーを実行するには、以下のいずれかの方法を選択できます：

#### 方法1: uvx（推奨）

uvは、Pythonパッケージとプロジェクトを管理するための高速なツールです。

**macOS / Linux:**
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

**Windows (PowerShell):**
```powershell
powershell -c "irm https://astral.sh/uv/install.ps1 | iex"
```

**インストールの確認:**
```bash
uv --version
```

**期待される出力例:**
```
uv 0.x.x
```

> 💡 **ヒント:** ターミナルを再起動して、PATHが正しく設定されていることを確認してください。

#### 方法2: pipx（uvの代替）

pipxは、Pythonアプリケーションを隔離環境で実行するツールです。uvがインストールできない場合に使用できます。

**インストール:**
```bash
pip install pipx
pipx ensurepath
```

**インストールの確認:**
```bash
pipx --version
```

> 💡 **注意:** pipxを使用する場合は、後述の設定ファイルで`uvx`を`pipx run`に置き換えてください。

#### 方法3: pip + 仮想環境（手動管理）

標準的なpipと仮想環境を使用する方法です。

**仮想環境の作成:**
```bash
python -m venv .venv
```

**仮想環境の有効化:**

macOS / Linux:
```bash
source .venv/bin/activate
```

Windows (PowerShell):
```powershell
.venv\Scripts\Activate.ps1
```

Windows (コマンドプロンプト):
```cmd
.venv\Scripts\activate.bat
```

**MCPサーバーのインストール:**
```bash
pip install ibm-watsonx-orchestrate-mcp-server
```

> 💡 **注意:** この方法を使用する場合は、後述の設定ファイルで`command`を`ibm-watsonx-orchestrate-mcp-server`に変更し、`args`を削除してください。

#### どの方法を選ぶべきか？

- **uvx（推奨）**: 最も簡単で高速。自動的に隔離環境を管理
- **pipx**: uvがインストールできない環境での代替
- **pip + 仮想環境**: 既存のPython環境を活用したい場合

> 📖 **詳細情報:** 各インストール方法の詳細は、[公式ドキュメント](https://developer.watson-orchestrate.ibm.com/mcp_server/wxOmcp_installation)を参照してください。

---

### ステップ3: MCP設定ファイルの作成

#### 3.1 設定ファイルの作成

`Users/user1/.bob/setting/mcp_setting.json`に、以下の内容をコピー＆ペーストします：

**方法1: uvxを使用する場合（推奨）**

```json
{
    "servers": {
        "wxo-mcp": {
            "command": "uvx",
            "args": [
                "--with",
                "ibm-watsonx-orchestrate==1.13.0",
                "ibm-watsonx-orchestrate-mcp-server"
            ],
            "env": {
                "WXO_MCP_WORKING_DIRECTORY": "/Users/your-username/your-workspace"
            }
        },
        "wxo-docs": {
            "command": "uvx",
            "args": [
                "mcp-proxy",
                "--transport",
                "streamablehttp",
                "https://developer.watson-orchestrate.ibm.com/mcp"
            ]
        }
    }
}
```

**方法2: pipxを使用する場合**

```json
{
    "servers": {
        "wxo-mcp": {
            "command": "pipx",
            "args": [
                "run",
                "--spec",
                "ibm-watsonx-orchestrate==1.13.0",
                "ibm-watsonx-orchestrate-mcp-server"
            ],
            "env": {
                "WXO_MCP_WORKING_DIRECTORY": "/Users/your-username/your-workspace"
            }
        },
        "wxo-docs": {
            "command": "pipx",
            "args": [
                "run",
                "mcp-proxy",
                "--transport",
                "streamablehttp",
                "https://developer.watson-orchestrate.ibm.com/mcp"
            ]
        }
    }
}
```

**方法3: pip + 仮想環境を使用する場合**

仮想環境を有効化した状態で、以下の設定を使用します：

```json
{
    "servers": {
        "wxo-mcp": {
            "command": "ibm-watsonx-orchestrate-mcp-server",
            "args": [],
            "env": {
                "WXO_MCP_WORKING_DIRECTORY": "/Users/your-username/your-workspace"
            }
        },
        "wxo-docs": {
            "command": "uvx",
            "args": [
                "mcp-proxy",
                "--transport",
                "streamablehttp",
                "https://developer.watson-orchestrate.ibm.com/mcp"
            ]
        }
    }
}
```

> ⚠️ **重要:** 方法3を使用する場合は、Bobを起動する前に仮想環境を有効化しておく必要があります。

#### 3.3 設定内容の説明

**wxo-mcp（watsonx Orchestrate ADK MCP）:**
- エージェント、ツール、ナレッジベースの作成・管理用
- STDIO接続（ローカル実行）
- `WXO_MCP_WORKING_DIRECTORY`: ファイルアクセスを許可するルートディレクトリ（**必ず実際のパスに変更してください**）

**wxo-docs（watsonx Orchestrate ADK Docs MCP）:**
- ドキュメント検索用
- HTTP接続（リモート実行）
- 公式ドキュメントへのアクセスを提供

> ⚠️ **重要:** `WXO_MCP_WORKING_DIRECTORY`は、実際のワークスペースの絶対パスに変更してください。例：
> - macOS/Linux: `/Users/username/projects/my-workspace`
> - Windows: `C:/Users/username/projects/my-workspace`

#### 3.4 ディレクトリの作成（必要に応じて）

`.bob`ディレクトリが存在しない場合は作成します：

**macOS / Linux:**
```bash
mkdir -p .bob
```

**Windows (PowerShell):**
```powershell
New-Item -ItemType Directory -Path .bob -Force
```

**Windows (コマンドプロンプト):**
```cmd
mkdir .bob
```

> 💡 **ヒント:** コマンドプロンプトの`mkdir`コマンドは、ディレクトリが既に存在する場合はエラーを表示しますが、実害はありません。

---

### ステップ4: Bobでの接続

#### 4.1 Bobの再起動

MCP設定を読み込むために、Bobを再起動します。

#### 4.2 MCPサーバーの確認

1. Bobで `Ctrl+P`（macOSでは `Cmd+P`）を押してコマンドパレットを開きます
2. `>MCP: List Servers` と入力して実行します
3. 以下の2つのサーバーが表示されることを確認します：
   - `wxo-mcp`
   - `wxo-docs`

#### 4.3 MCPサーバーの起動

各サーバーの横にある「Start Server」ボタンをクリックして起動します。

> 💡 **ヒント:** 初回起動時は、uvxが必要なパッケージを自動的にダウンロード・インストールするため、少し時間がかかる場合があります。

---

### ステップ5: 動作確認

#### 5.1 MCPツールの確認

Bobのチャット画面で、MCPツールが利用可能になっていることを確認します。以下のようなツールが表示されるはずです：

**wxo-mcp（watsonx Orchestrate ADK MCP）のツール例:**
- `list_agents`: エージェント一覧の取得
- `create_or_update_agent`: エージェントの作成・更新
- `list_tools`: ツール一覧の取得
- `import_tool`: ツールのインポート
- など

**wxo-docs（watsonx Orchestrate ADK Docs MCP）のツール例:**
- `search_ibm_watsonx_orchestrate_adk`: ドキュメント検索
- `query_docs_filesystem_ibm_watsonx_orchestrate_adk`: ドキュメントファイルシステムへのクエリ

#### 5.2 テスト実行

Bobのチャットで以下のように質問して、MCPツールが正常に動作するか確認します：

```
watsonx Orchestrateのエージェント一覧を取得してください
```

または

```
watsonx Orchestrate ADKのドキュメントで「agent」について検索してください
```

---

## トラブルシューティング

### 問題1: MCPサーバーが起動しない

**原因:** uvx/pipxがインストールされていない、またはPATHが設定されていない

**解決策:**
1. 使用しているコマンドのバージョンを確認
   - uvxの場合: `uv --version`
   - pipxの場合: `pipx --version`
2. インストールされていない場合は、[ステップ2](#ステップ2-mcpサーバー実行環境のセットアップ)を実行
3. ターミナルを再起動してPATHを更新
4. それでも解決しない場合は、[方法3（pip + 仮想環境）](#ステップ2-mcpサーバー実行環境のセットアップ)を試してください

### 問題2: ファイルアクセスエラー

**原因:** `WXO_MCP_WORKING_DIRECTORY`が正しく設定されていない

**解決策:**
1. `.bob/mcp.json`の`WXO_MCP_WORKING_DIRECTORY`を実際のワークスペースの絶対パスに変更
2. Bobを再起動
3. MCPサーバーを再起動

### 問題3: watsonx Orchestrate環境に接続できない

**原因:** ADKの設定ファイルが存在しない、または認証情報が無効

**解決策:**
1. `~/.orchestrate/config.yaml`が存在するか確認
2. 存在しない場合は、[watsonx Orchestrate ADKのセットアップ](https://developer.watson-orchestrate.ibm.com/getting_started/installing)を完了
3. 認証情報が有効か確認（必要に応じて再ログイン）

### 問題4: 「.bob/mcp.json」が認識されない

**原因:** Bobが`.bob`ディレクトリをサポートしていない可能性

**解決策:**
1. `.vscode/mcp.json`に設定ファイルを作成
2. 同じ内容を記述
3. Bobを再起動

---

## 参考リンク

### 公式ドキュメント
- [watsonx Orchestrate ADK MCP Server - インストール](https://developer.watson-orchestrate.ibm.com/mcp_server/wxOmcp_installation)
- [watsonx Orchestrate ADK MCP Server - 統合](https://developer.watson-orchestrate.ibm.com/mcp_server/wxOmcp_integration)
- [watsonx Orchestrate ADK MCP Server - 設定](https://developer.watson-orchestrate.ibm.com/mcp_server/wxOmcp_configuration)
- [watsonx Orchestrate ADK - Getting Started](https://developer.watson-orchestrate.ibm.com/getting_started/installing)

### その他のリソース
- [Model Context Protocol 公式サイト](https://modelcontextprotocol.io/)
- [uv - Python Package Manager](https://github.com/astral-sh/uv)

---

## 次のステップ

MCP設定が完了しました。次は、ContentIQをセットアップします。

➡️ **[ContentIQセットアップガイド](contentiq-setup.md)**

---

**ナビゲーション:**
- [← watsonx Orchestrateセットアップ](orchestrate-setup.md)
- [← README に戻る](../README.md)
- [ContentIQセットアップ →](contentiq-setup.md)

---

© 2026 IBM watsonx Orchestrate セットアップガイド