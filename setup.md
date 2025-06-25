# サイト作成の準備

<div style="background-color: #d4edda; padding: 15px; border-radius: 5px; margin: 15px 0;">
<strong>⏱️ 所要時間: 約30分</strong><br>
GitHub アカウント作成（10分）+ サイト設定（15分）+ 動作確認（5分）<br>
<small>※初回は GitHub の操作に慣れるまで追加で10-15分かかる場合があります</small>
</div>

このページでは、GitHub Pages を使った社会連携講座サイトの作成手順を説明します。

<div style="background-color: #fff2e6; padding: 15px; border-radius: 5px; margin: 15px 0;">
<strong>🏫 研究機関での利用について</strong><br>
所属機関の情報セキュリティポリシーを事前に確認してください。パブリックリポジトリでは全ての情報が公開されます。機密性の高い情報は掲載しないよう注意が必要です。
</div>

## ステップ1: GitHub アカウント作成

### 1-1. GitHub サイトにアクセス
[https://github.com](https://github.com) にアクセスします。

### 1-2. アカウント作成
1. 「Sign up」をクリック
2. **Username**: 講座名やグループ名を含む分かりやすい名前
   - 例：`tokyo-univ-social-cooperation`
3. **Email**: 連絡可能なメールアドレス
4. **Password**: 強固なパスワード

### 1-3. アカウント認証
- メール認証を完了させます
- 「Verify email address」をクリック

## ステップ2: テンプレートリポジトリの利用

### 2-1. テンプレートの選択
新規作成よりも**テンプレートを使用することを強く推奨**します。

<div style="background-color: #e3f2fd; padding: 15px; border-radius: 5px; margin: 15px 0;">
<strong>📍 テンプレートの場所</strong><br>
このマニュアルサイト自体がテンプレートです。ブラウザの上部URLバーにある GitHub リポジトリページで「Use this template」ボタンを探してください。
</div>

1. **このページの GitHub リポジトリ**にアクセス（画面上部のリンクから）
2. 緑色の「Use this template」ボタンをクリック
3. 「Create a new repository」を選択

### 2-2. リポジトリ設定
1. **Repository name**: `[講座名]-website`
   - 例：`social-cooperation-website`
2. **Description**: 「社会連携講座の活動報告サイト」
3. **Public** を選択（GitHub Pages の無料利用に必要）
4. **Include all branches**: チェックしない
5. 「Create repository」をクリック

## ステップ3: GitHub Pages 有効化

### 3-1. Settings にアクセス
1. 作成したリポジトリのページで「Settings」タブをクリック
2. 左側メニューの「Pages」をクリック

### 3-2. Source 設定
1. **Source**: "Deploy from a branch" を選択
2. **Branch**: "main" を選択
3. **Folder**: "/ (root)" を選択
4. 「Save」をクリック

### 3-3. 公開 URL の確認
- 数分後に `https://[ユーザー名].github.io/[リポジトリ名]` でアクセス可能
- 例：`https://tokyo-univ-social.github.io/social-cooperation-website`

## ステップ4: 基本設定ファイルの編集

### 4-1. _config.yml の編集
リポジトリの `_config.yml` ファイルを編集：

```yaml
title: [講座名]の活動報告サイト
author: [責任者名]
description: [講座の簡単な説明]

theme: minima
markdown: CommonMarkGhPages
commonmark:
  options: ["UNSAFE", "SMART", "FOOTNOTES"]
  extensions: ["strikethrough", "autolink", "table", "tagfilter"]

plugins:
  - jekyll-feed
  - jekyll-titles-from-headings

titles_from_headings:
  strip_title: true
  collections: false
```

### 4-2. 編集方法
1. `_config.yml` ファイルをクリック
2. 右上の ✏️（鉛筆アイコン）をクリック
3. 内容を編集
4. ページ下部で変更をコミット

## ステップ5: 初期ページの作成

### 5-1. トップページ（index.md）
```markdown
---
layout: home
title: [講座名]
---

# [講座名]へようこそ

## 講座について
ここに講座の概要を記載します。

## 最新情報
最新の議事録やお知らせは下記をご覧ください。
```

### 5-2. About ページ（about.md）
```markdown
---
layout: page
title: 講座について
---

# 講座について

## 目的
[講座の目的を記載]

## 活動内容
[主な活動内容を記載]

## メンバー
[メンバー情報を記載]
```

## ステップ6: 動作確認

### 6-1. サイトの表示確認
1. ブラウザで公開URLにアクセス
2. ページが正しく表示されることを確認
3. ナビゲーションメニューの動作確認

### 6-2. よくある問題
| 問題 | 原因 | 解決方法 |
|------|------|----------|
| 404 エラー | GitHub Pages 未有効化 | Settings → Pages で設定確認 |
| デザインが崩れる | _config.yml エラー | YAML 記法を確認 |
| 更新されない | 反映時間 | 5-10分待つ |

## セキュリティ設定

### リポジトリのアクセス権限
1. **Settings** → **Manage access**
2. 必要に応じて共同編集者を追加
3. **Write** 権限を付与

### ブランチ保護（推奨）
1. **Settings** → **Branches**
2. **Add rule** で main ブランチを保護
3. **Require pull request reviews** をチェック

## 次のステップ

サイトが正常に作成できたら、[CommonMark 記法](commonmark-guide) で文書作成の基本を学びましょう。

---

## トラブルシューティング

### Q: リポジトリが作成できません
A: ユーザー名やリポジトリ名に使用できない文字が含まれている可能性があります。英数字とハイフンのみ使用してください。

### Q: GitHub Pages の設定が見つかりません
A: リポジトリが Private になっている可能性があります。Public に変更してください。

### Q: サイトが表示されません
A: DNS の反映に時間がかかることがあります。24時間ほど待ってから再度確認してください。

**次のステップ**: [CommonMark 記法](commonmark-guide) で文書作成方法を学びましょう。