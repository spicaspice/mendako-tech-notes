# OpenClawの設定方法

## 概要

OpenClaw の基本セットアップは、`install.sh` で本体を入れて、`openclaw onboard --install-daemon` で初期設定する流れです。最短なら、インストール、オンボーディング、Gateway 起動確認、Control UI 確認の4段階で始められます。

## 詳細説明

2026年6月6日時点で見た公式系ドキュメントでは、まず Node.js 22 以上、または推奨の Node 24 系が前提です。

### 1. インストール

macOS / Linux なら、いちばん簡単なのはこれです。

```bash
curl -fsSL https://openclaw.ai/install.sh | bash
```

Windows PowerShell の場合は次です。

```powershell
iwr -useb https://openclaw.ai/install.ps1 | iex
```

すでに Node 環境を自分で管理しているなら、npm で入れる方法もあります。

```bash
npm install -g openclaw@latest
```

### 2. 初期設定

インストール後はオンボーディングを実行します。

```bash
openclaw onboard --install-daemon
```

このセットアップで主にやることは次の3つです。

- 利用する LLM の API キーや接続先を設定する
- Gateway を常駐サービスとして入れる
- Slack や WhatsApp など必要なチャネル連携を進める

### 3. 動作確認

インストール後は次のコマンドで確認できます。

```bash
openclaw --version
openclaw doctor
openclaw gateway status
```

手早く試すなら Control UI を開くのが楽です。

```bash
openclaw dashboard
```

Gateway ホスト上なら、ブラウザで `http://127.0.0.1:18789/` を開いて確認できます。

### 4. 開発者向けの入れ方

本体を触りたい場合は GitHub から clone して入れる方法もあります。

```bash
git clone https://github.com/openclaw/openclaw.git
cd openclaw
pnpm install
pnpm build
pnpm ui:build
pnpm link --global
openclaw onboard --install-daemon
```

### 5. つまずきやすい点

- `openclaw` コマンドが見つからない: PATH かグローバルインストール周りを確認する
- Gateway が起動しない: `openclaw doctor` と `openclaw gateway status` で状態を見る
- まず触ってみたいだけ: 先に `openclaw dashboard` で Control UI を使うと、チャネル連携なしでも試しやすい

## 参照URL

- https://github.com/openclaw/openclaw/blob/main/docs/install/index.md
- https://clawdocs.org/getting-started/installation/
- https://openclawlab.com/en/docs/start/getting-started/
