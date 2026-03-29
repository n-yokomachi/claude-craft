# claude-harness

Claude Code のカスタムスキル・設定ファイル一式を管理し、シンボリックリンクで `~/.claude/` へデプロイするハーネスプロジェクトです。

## セットアップ

```bash
# このリポジトリを clone
git clone <repo-url>
cd claude-harness

# Claude Code 上でインストーラを実行
/harness-init

# ターミナル環境のセットアップ（Ghostty + tmux + yazi + lazygit）
/terminal-init
```

## プロジェクト構造

```
claude-harness/
├── dotfiles/                   # ~/.claude/ に配置するファイル群
│   ├── CLAUDE.md               #   グローバル指示ファイル
│   ├── settings.json           #   Claude Code 設定
│   ├── statusline-command.sh   #   ステータスライン（TokyoNight テーマ）
│   ├── ghostty/config          #   Ghostty ターミナル設定
│   ├── tmux.conf               #   tmux 設定
│   ├── yazi/yazi.toml          #   yazi ファイルマネージャ設定
│   └── lazygit/config.yml      #   lazygit 設定
├── skills/                     # ~/.claude/skills/ に配置するスキル群
│   ├── briefing/               #   朝のブリーフィング（予定・メール・天気）
│   ├── calendar/               #   カレンダー確認
│   └── email-check/            #   メールチェック
├── .claude/skills/
│   ├── harness-init/           #   Claude Code 設定デプロイ（プロジェクトレベル）
│   └── terminal-init/          #   ターミナル環境構築（プロジェクトレベル）
└── CLAUDE.md                   # プロジェクト固有の指示
```

## スキル一覧

| スキル | 説明 |
|--------|------|
| `/harness-init` | Claude Code 設定を `~/.claude/` にデプロイ |
| `/terminal-init` | Ghostty + tmux + yazi + lazygit のインストールと設定 |
| `/briefing` | 今日の予定・メール・天気をまとめて報告 |
| `/calendar` | Google Calendar の予定を確認 |
| `/email-check` | Gmail の受信トレイを確認 |

## 外部連携

| サービス | 方式 |
|----------|------|
| Gmail | クラウド MCP（Anthropic 提供） |
| Google Calendar | クラウド MCP（Anthropic 提供） |
| Slack | クラウド MCP（Anthropic Slack Connector） |

## 開発フロー

1. `skills/` や `dotfiles/` のファイルを編集
2. `/harness-init` で Claude Code 設定を `~/.claude/` に反映
3. `/terminal-init` でターミナル環境をセットアップ
4. 別プロジェクトで動作確認

設定ファイルはシンボリックリンクで配置されるため、リポジトリを `git pull` するだけで全環境に反映されます。

## シークレット管理

`settings.json` にシークレットは含めません。API キー等はシェルプロファイル（`~/.zshrc` など）で `export` してください。
