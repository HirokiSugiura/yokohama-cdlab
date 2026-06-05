# GitHub Pages セットアップ手順書

> yokohama-cdlab リポジトリを公開するまでの手順
> 所要時間：約30分（Git初回設定済みの場合は15分）

---

## 前提確認

| 項目 | 確認方法 |
|---|---|
| GitHubアカウント | https://github.com にログインできること |
| Git（ローカルインストール）| ターミナルで `git --version` が返ること |
| ターミナル操作 | macOS：ターミナル.app、またはVS Code内ターミナル |

Git未インストールの場合は https://git-scm.com からインストール。

---

## STEP 1：GitHubでリポジトリを作成

1. https://github.com/new にアクセス
2. 以下のように設定：

   | 項目 | 設定値 |
   |---|---|
   | Repository name | `yokohama-cdlab` |
   | Description | 横浜コミュニティデザイン・ラボ ナレッジコモンズ |
   | Visibility | **Public**（GitHub Pagesは無料プランでPublicのみ対応） |
   | Initialize this repository | **チェックしない**（ローカルからpushするため） |

3. **「Create repository」**をクリック

> 作成後に表示されるURL（例：`https://github.com/hamakei/yokohama-cdlab`）を控えておく。

---

## STEP 2：ローカルにフォルダを準備

ターミナルを開いて以下を実行。

```bash
# 作業ディレクトリに移動（例：デスクトップ）
cd ~/Desktop

# リポジトリ用フォルダを作成
mkdir yokohama-cdlab
cd yokohama-cdlab

# Gitを初期化
git init

# フォルダ構成を作成
mkdir knowledge projects history templates
```

---

## STEP 3：ファイルをコピー

Obsidian の `outputs/github-pages/` フォルダの中身を、作成した `yokohama-cdlab/` フォルダにコピーする。

**Finderでコピーする場合：**

```
コピー元：Obsidian Vault/01-Projects/横浜CDラボ/outputs/github-pages/
コピー先：~/Desktop/yokohama-cdlab/
```

コピー後のフォルダ構成：

```
yokohama-cdlab/
├── README.md
├── knowledge/
│   └── cowork-obsidian-npo.md
├── projects/
├── history/
└── templates/
```

**ターミナルでコピーする場合：**

```bash
# Obsidian VaultのパスはVaultの設定で確認する
cp -r ~/path/to/obsidian/01-Projects/横浜CDラボ/outputs/github-pages/. ~/Desktop/yokohama-cdlab/
```

---

## STEP 4：GitHubにpush

```bash
cd ~/Desktop/yokohama-cdlab

# ファイルをステージング
git add .

# コミット
git commit -m "initial commit: ナレッジコモンズ初版"

# ブランチ名を main に設定（GitHub のデフォルトに合わせる）
git branch -M main

# リモートリポジトリを登録（URLは STEP 1 で控えたもの）
git remote add origin https://github.com/【あなたのユーザー名】/yokohama-cdlab.git

# push
git push -u origin main
```

> 初回pushでGitHubの認証が求められた場合：
> - ブラウザでGitHubにログインした状態でターミナルの指示に従う
> - または Personal Access Token（Settings → Developer settings → Tokens）を使用

---

## STEP 5：GitHub Pagesを有効化

1. GitHubのリポジトリページ（`https://github.com/【ユーザー名】/yokohama-cdlab`）を開く
2. **Settings**タブ → 左メニュー **Pages**
3. **Source** を `Deploy from a branch` に設定
4. **Branch** を `main` / `/ (root)` に設定して **Save**

数分後、以下のURLでサイトが公開される：

```
https://【ユーザー名】.github.io/yokohama-cdlab/
```

> GitHub側の反映に最大10分かかる場合がある。

---

## STEP 6（任意）：独自ドメインを設定

`yokohama-cdl.org` などを取得済みの場合：

1. リポジトリのルートに `CNAME` ファイルを作成し、ドメイン名のみを記述

   ```
   cdlab.yokohama-cdl.org
   ```

2. ドメインのDNS設定で CNAME レコードを追加：

   ```
   CNAME → 【ユーザー名】.github.io
   ```

3. GitHubの Settings → Pages → Custom domain に入力して Save

---

## 今後の更新フロー

記事を追加・更新するときは：

```bash
cd ~/Desktop/yokohama-cdlab

# ファイルを追加・編集後
git add .
git commit -m "knowledge: 記事タイトルを追加"
git push
```

pushするとGitHub Pagesに自動反映される（数分後）。

---

## トラブルシューティング

| 症状 | 対処 |
|---|---|
| `git push` で403エラー | GitHubへのログイン・認証を確認。Personal Access Tokenが必要な場合あり |
| Pagesが表示されない | Settings → Pages でSourceが正しく設定されているか確認 |
| 日本語ファイル名が文字化け | ターミナルで `git config core.quotepath false` を実行 |
| pushしたが反映されない | GitHub Actions タブでビルドエラーがないか確認 |

---

*作成：2026-06-05｜横浜コミュニティデザイン・ラボ*
