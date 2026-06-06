# エルメスエージェントの設定

## 概要

Hermes Agent の基本設定は、インストールして `hermes setup` を実行し、使うモデルプロバイダを選んで、必要なら Gateway や各種ツールを有効化する流れです。2026年6月6日時点で、いちばん速い導線としては `hermes setup --portal` が公式ドキュメントで強く案内されています。

## 詳細説明

ここでいうエルメスエージェントは、Nous Research の `Hermes Agent` のことです。公式ドキュメントでは「self-improving AI agent」として案内されていて、CLI で動き、モデル、ツール、Gateway、Skills を組み合わせて使います。

### 1. インストール

公式の基本インストールはこれです。

```bash
curl -fsSL https://raw.githubusercontent.com/NousResearch/hermes-agent/main/scripts/install.sh | bash
```

その後、必要なら追加セットアップもできます。

```bash
hermes postinstall
```

これは任意ですが、ドキュメント上では Node.js、browser、`ripgrep`、`ffmpeg` などの周辺依存を入れる補助として案内されています。

### 2. 最短セットアップ

いちばん簡単な方法は Nous Portal を使う流れです。

```bash
hermes setup --portal
```

このセットアップでは、公式ドキュメントによると次のことが行われます。

- ブラウザで Nous Portal にログイン
- 認証トークンを `~/.hermes/auth.json` に保存
- `~/.hermes/config.yaml` にプロバイダ設定を入れる
- Tool Gateway を有効化する
- そのまま `hermes chat` を始められる状態にする

Portal を使わない場合でも、通常のセットアップは次で進められます。

```bash
hermes setup
```

### 3. 設定コマンド

Hermes は設定対象ごとにコマンドが分かれています。CLI リファレンス上では次のような形です。

```bash
hermes setup [model|tts|terminal|gateway|tools|agent]
```

たとえば、

- `hermes setup model`
- `hermes setup gateway`
- `hermes setup tools`

のように分けて再設定できます。

### 4. 動作確認

セットアップ後は次を確認すると分かりやすいです。

```bash
hermes
hermes chat
hermes model
hermes portal status
```

モデル設定の確認や切り替えは `hermes model`、Portal を使っている場合の接続確認は `hermes portal status` が近道です。

### 5. OpenClaw からの移行

もし OpenClaw を使っていたなら、Hermes Agent は `~/.openclaw` を見つけて移行を案内できます。GitHub の README では、初回セットアップ時に自動検出して移行を提案すると案内されています。

手動移行コマンドの例:

```bash
hermes claw migrate
hermes claw migrate --dry-run
hermes claw migrate --preset user-data
```

移行対象には、`SOUL.md`、メモリ、ユーザー作成スキル、コマンド許可設定、メッセージング設定、許可された API キーなどが含まれます。

### 6. つまずきやすい点

- `hermes` コマンドが見つからない: PATH やインストール完了を確認する
- リモートサーバーで `--portal` がうまくいかない: OAuth なので SSH ポートフォワーディングや manual paste が必要になることがある
- モデルが未設定: `hermes setup` か `hermes model` で設定する
- Web や画像系ツールが動かない: Gateway や tools の設定が未完了のことがある

## 参照URL

- https://hermes-agent.nousresearch.com/docs/
- https://hermes-agent.nousresearch.com/docs/integrations/nous-portal
- https://hermes-agent.nousresearch.com/docs/guides/run-hermes-with-nous-portal
- https://hermes-agent.nousresearch.com/docs/user-guide/configuring-models
- https://github.com/NousResearch/hermes-agent
