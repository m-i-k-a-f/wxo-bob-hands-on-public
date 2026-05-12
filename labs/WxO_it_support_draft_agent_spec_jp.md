# ITサポートマルチエージェントアプリケーション仕様書

## 概要

Watsonx Orchestrateで実行されるマルチエージェントITサポートアプリケーションのプロトタイプを作成します。

## プロトタイプの特徴

これはプロトタイプであるため、以下のコンポーネントをハードコードします：

- サンプルのITサポートチケット
- デバイスとアカウントのステータスデータ
- ツールの戻り値

### サポートシナリオのカテゴリ

サンプルサポートシナリオは以下のカテゴリをカバーする必要があります：

- パスワードリセット
- アカウントロックアウト
- ソフトウェアインストール
- VPNアクセス
- Wi-Fi接続
- メールの問題
- プリンターの問題
- ラップトップのパフォーマンス
- ハードウェアトラブルシューティング
- アクセス要求

## エージェント実装の詳細

### 1. エージェントの実装形式

- エージェントの指示はYAMLで実装されます
- YAMLガイドライン: https://developer.watson-orchestrate.ibm.com/agents/build_agent

### 2. エージェント構成

3つのエージェントを作成します：

1. `incident_response_agent`
2. `pc_support_agent`
3. `it_support_agent`（オーケストレーター）

### 3. 各エージェントの詳細

#### 3.1 incident_response_agent

**責任範囲：** 技術的な問題に関する質問への回答とインシデントチケットの作成

**ツール：**

##### a. check_open_incidents()
- **機能：** オープンまたは最近のITインシデントをリスト
- **戻り値：** 現在オープンまたは注意が必要な最大3つのインシデント

##### b. create_incident_ticket()
- **機能：** 新しいITサポートケースを開く
- **戻り値：** サンプルチケット番号を含む確認

#### 3.2 pc_support_agent

**責任範囲：** PCのトラブルシューティングとソフトウェア関連の問題を支援

**ツール：**

##### a. diagnose_pc_issue()
- **機能：** PC全般の問題（起動、パフォーマンス、エラー）を診断
- **戻り値：** 診断結果と推奨される対処法

##### b. check_software_compatibility()
- **機能：** ソフトウェアの互換性とインストール状況を確認
- **戻り値：** 互換性情報とインストール推奨事項

#### 3.3 it_support_agent

**責任範囲：** `incident_response_agent`と`pc_support_agent`をオーケストレート

## 4. ツールの実装

### 4.1 実装言語

ツールはPythonで実装されます。

### 4.2 ツール実装の構文

```python
#test_tool.py
from ibm_watsonx_orchestrate.agent_builder.tools import tool


@tool()
def my_tool(input: str) -> str:
    """提供された入力に基づいてツールのアクションを実行します。

    Args:
        input (str): ツールの入力。

    Returns:
        str: ツールのアクション。
    """

    #ツールの機能

    return f"Hello, {input}"
```

### 4.3 戻り値

ツールはハードコードされた値を返す必要があります。

## 5. ファイル構成

### エージェントファイル

- 保存先：`/agents`フォルダ
- 形式：YAML

### ツールファイル

- 保存先：`/tools`フォルダ
- 形式：Python

## 6. ドキュメント

実装を説明するMarkdownファイルを生成します。

### 7. Markdownファイルの内容

#### a. 実装の詳細

実装の詳細を記述します。

#### b. デプロイ手順

**ツールインポートコマンド：**
```bash
orchestrate tools import -k python -f <file_name>.py
```

**エージェントインポートコマンド：**
```bash
orchestrate agents import -f <file_name>.yaml
```

#### c. サンプル質問

エージェントが回答できる5〜10のサンプル質問を記載します。