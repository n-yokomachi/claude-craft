---
name: terminal-init
description: ターミナル環境（Ghostty + tmux）のインストールと設定を行う。ターミナルセットアップ、Ghostty設定、tmux設定に使用。
allowed-tools: Bash, Read, Write, Edit, Glob
---

# Terminal Init

Ghostty + tmux のインストールと設定ファイルの配置を行う。

## 実行手順

### Step 1: OS検出とパッケージマネージャ確認

1. OS検出（macOS / Linux）
2. パッケージマネージャの確認:
   - macOS: `brew`
   - Linux: `apt` / `dnf` / `pacman` など
3. ※ GhosttyはWindows非対応。Windowsの場合はその旨を報告して終了。

### Step 2: インストール

既にインストール済みかどうかを確認し、未インストールのもののみインストールする。

**macOS:**
```bash
brew install --cask ghostty
brew install tmux
```

**Linux (apt例):**
```bash
# Ghostty: 公式サイトの手順に従う
# tmux
sudo apt install tmux
```

### Step 3: 設定ファイルの配置

ハーネスリポジトリ内の設定ファイルをシンボリックリンクで配置する。

**Ghostty:**
```bash
# macOS
ln -sf <repo>/dotfiles/ghostty/config "$HOME/Library/Application Support/com.mitchellh.ghostty/config"

# Linux
mkdir -p ~/.config/ghostty
ln -sf <repo>/dotfiles/ghostty/config ~/.config/ghostty/config
```

**tmux:**
```bash
ln -sf <repo>/dotfiles/tmux.conf ~/.tmux.conf
```

※ 設定ファイルが `<repo>/dotfiles/` に存在しない場合はスキップし、手動設定が必要な旨を報告する。

### Step 4: 検証と報告

1. `ghostty --version` と `tmux -V` でインストール確認
2. 設定ファイルのシンボリックリンク状態を `ls -la` で確認
3. Claireの口調で結果を報告
