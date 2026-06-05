# Claude in Chrome 指示プロンプト

以下をそのままClaude in Chromeに貼り付けて使う。

---

## 【指示①】新しいpublicリポジトリを作成する

```
GitHubで新しいリポジトリを作成してください。

設定：
- Repository name: yokohama-cdlab
- Description: 横浜コミュニティデザイン・ラボ ナレッジコモンズ
- Visibility: Public（必ずPublicにすること）
- Initialize: README.mdのチェックはしない

https://github.com/new を開いて、上記の設定で「Create repository」ボタンを押すまで進めてください。
```

---

## 【指示②】GitHub Pagesを有効化する（リポジトリ作成・push完了後に使う）

```
GitHubリポジトリ https://github.com/HirokiSugiura/yokohama-cdlab のGitHub Pagesを有効化してください。

手順：
1. 上記URLのリポジトリを開く
2. 「Settings」タブをクリック
3. 左メニューの「Pages」をクリック
4. 「Source」を「Deploy from a branch」に設定
5. Branch を「main」、フォルダを「/ (root)」に設定
6. 「Save」をクリック

完了したら、公開URLを教えてください。
```

---

## 【指示③】obsidian-memoをpublicに変更する場合（①の代わりに使う）

```
GitHubリポジトリ https://github.com/HirokiSugiura/obsidian-memo の公開設定をPrivateからPublicに変更してください。

手順：
1. 上記URLを開く
2. 「Settings」タブをクリック
3. 一番下の「Danger Zone」セクションを開く
4. 「Change visibility」をクリック
5. 「Make public」を選択して確認操作を進める

※ただし、個人メモが含まれる場合は公開前に内容を確認すること。
```

---

## 補足

- **指示①→push→指示②** の順番が推奨フロー
- obsidian-memoはバックアップ用privateのまま残して、コモンズ用に新しくyokohama-cdlabを作るのがすっきりする
- pushはターミナルで手動実行が必要（Claude in Chromeはローカルのgitコマンドを実行できない）
