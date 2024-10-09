# README

## はじめに

このリポジトリには、リアルタイムAPIの使用を簡単にするために設計されたカスタムクライアントの使用例を示すサンプルコードが含まれています。以下の2つの主なサンプルが含まれています:

1. `low_level_sample.py` - このファイルは、APIとやり取りするために `LowLevelClient` を使用しています。
2. `client_sample.py` - このファイルは、現在進行中の作業である上位レベルの `RTClient` の使用例を示しています。`RTClient` は、APIの利用を簡素化するための抽象化を提供する便利なレイヤーとして設計されています。

## セットアップ手順

### 1. 仮想環境の作成と有効化

依存関係を適切に管理するために、仮想環境の使用を推奨します。以下の手順に従って、仮想環境を作成し、有効化します:


```sh
# Create a virtual environment
python3 -m venv venv

# Activate the virtual environment
source venv/bin/activate
```

### 2. 依存関係のインストール

仮想環境を有効にした後、提供されているスクリプトを使用して最新のパッケージホイールをダウンロードし、`pip` を使用して必要な依存関係をインストールします:

- bash 用: [download-pkg.sh](./download-pkg.sh)
    > このスクリプトを実行するには、`jq` がインストールされている必要があります。

- PowerShell 用: [download-pkg.ps1](./download-pkg.ps1)

それぞれ、`./download-pkg.sh` または `pwsh ./download-pkg.ps1` と入力して実行できます。


次に、依存関係をインストールします:
```sh
pip install -r requirements.txt
pip install rtclient-0.4.0-py3-none-any.whl
```

### 3. 環境変数の設定

このアプリケーションには、いくつかの環境変数の設定が必要です。これらの変数は `.env` ファイルに定義できます。リポジトリには `development.env` というテンプレートファイルが含まれています。以下の手順に従って `.env` ファイルを設定してください:

1. `development.env` テンプレートを `.env` という名前の新しいファイルにコピーします:

    ```sh
    cp development.env .env
    ```

2. テキストエディタで `.env` ファイルを開き、必要な値を入力します。テンプレートには必要な環境変数のプレースホルダーが含まれています。

### 4. サンプルの実行

- ローレベルクライアントサンプルを実行するには:

    ```sh
    python low_level_sample.py <audio file> <azure|openai>
    ```

    `<audio file>` は実行時に使用される入力音声ファイルです（サポートされている形式のサンプルファイルがリポジトリに含まれています）。

    最後のパラメーターは `azure` または `openai` のいずれかで、Azure OpenAI または OpenAI に対してサンプルを実行するかどうかを示します。

- ハイレベルクライアントサンプルを実行するには:

    ```sh
    python client_sample.py <audio_file> <out_dir> <azure|openai>
    ```

    パラメーターは `low_level_client.py` と同じですが、`<out_dir>` という追加のパラメーターがあり、これは実行のすべての出力が保存される既存のディレクトリです。


## 注意事項

- `RTClient` は現在開発中であり、APIの利用を簡素化するために、より高レベルの抽象化を提供することを目的としています。
- サンプルを実行する前に、`.env` ファイルが必要な認証情報と設定で正しく入力されていることを確認してください。

