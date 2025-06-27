# 社会連携講座向け GitHub Pages 運用マニュアル

このサイトは **Jekyll + Minima + CommonMarkGhPages** を使用した GitHub Pages サイトです。  
**社会連携講座の活動報告・議事録共有を目的とした非情報系理系研究者向け運用マニュアル**として構成されています。

🔗 **サイトURL**: https://utsoraji.github.io/githubpagesdemo/

## 📋 マニュアル構成

### 🏠 **トップページ** (`index.md`)
- このマニュアルについて
- 社会連携講座での活動報告サイト運用ガイド
- Jekyll + Minima テーマの利点
- マニュアルの進め方

### 📖 **GitHub Pages + Jekyll とは** (`about-system.md`)
- GitHub Pages の概要
- Jekyll の仕組み（Markdown → HTML 自動変換）
- Minima テーマの特徴
- CommonMarkGhPages の利点（表・脚注・取り消し線対応）

### 🚀 **サイト作成の準備** (`setup.md`)
- GitHub アカウント作成
- テンプレートリポジトリの利用
- _config.yml の基本設定
- GitHub Pages 有効化

### ✏️ **CommonMark 記法** (`commonmark-guide.md`)
- 基本的な Markdown 記法
- **CommonMarkGhPages 拡張機能**：
  - 表（table）の作成
  - 脚注（footnotes）の使い方
  - 取り消し線（strikethrough）
  - 自動リンク（autolink）
- HTMLとの併用（`<br>`、`<span style="">`など）

### 📝 **ページ管理** (`page-management.md`)
- Front Matter が不要な設定について
- ファイル構成とURL構造
- ナビゲーションへの追加方法
- ページタイトルの自動生成

### 📰 **投稿機能（議事録・お知らせ）** (`posts.md`)
- _posts フォルダの活用
- layout: post の使い方
- 日付とファイル名の規則
- トップページでの投稿一覧表示

### 📁 **ファイル・資料管理** (`file-management.md`)
- assets フォルダの構成
- 画像ファイルの配置・表示
- **GitHub Releases での PDF 管理**
- ダウンロードリンクの作成

### ⚙️ **_config.yml 設定詳細** (`configuration.md`)
- サイト基本情報（title, author, description）
- Minima テーマ設定
- CommonMarkGhPages オプション詳細：
  - UNSAFE（HTML混在許可）
  - SMART（スマート引用符）
  - FOOTNOTES（脚注機能）
- プラグイン設定（jekyll-feed, jekyll-titles-from-headings）

### 🎨 **Minima テーマカスタマイズ** (`minima-customization.md`)
- 非情報系研究者向けの安全なカスタマイズ
- 色合いとフォントサイズの調整
- ロゴ画像の追加
- ローカル編集環境構築後に実施する内容

### 🔄 **更新作業** (`update-operations.md`)
- Web エディタでの編集（基本）
- ローカル編集環境の構築（応用）
- FTPとの対比によるGit運用の理解
- **GitHub Releases での報告書PDF管理**
- 複数人での管理

### ❓ **トラブルシューティング** (`troubleshooting.md`)
- Jekyll ビルドエラーの対処
- CommonMarkGhPages 特有の問題
- Minima テーマでの表示問題
- 自己解決のための情報収集方法

### 📋 **社会連携講座向けテンプレート** (`templates.md`)
- 講座概要ページテンプレート
- 議事録投稿テンプレート（Front Matterは最小限）
- メンバー紹介ページテンプレート
- 報告書一覧ページテンプレート（GitHub Releases リンク付き）
- 削除されたabout.mdとpublications.mdの記述例

---

## 技術スタック

- **GitHub Pages**: 無料ホスティング
- **Jekyll**: 静的サイトジェネレータ
- **Minima**: シンプルで清潔なテーマ
- **CommonMarkGhPages**: GitHub Flavored Markdownに近い拡張Markdown（表・脚注・取り消し線対応）

---

## 対象読者

- PCの基本操作ができる方
- HTMLの存在を知っている程度の初心者
- 社会連携講座で活動報告・議事録共有のウェブサイト運用を担当する方

---

## 📖 詳細な運用手順（旧マニュアル）

以下は参考情報として残しています。新しいマニュアル構成の各ページで詳しく解説する予定です。

### 基本的な更新方法

### 🌐 GitHub上での編集（推奨）

1. **GitHub にログイン**
   - https://github.com にアクセス
   - アカウントでログイン

2. **リポジトリにアクセス**
   - このプロジェクトのリポジトリページを開く

3. **ファイルを編集**
   - 編集したいファイルをクリック
   - 右上の ✏️ (編集) ボタンをクリック
   - 内容を修正

4. **変更を保存**
   - ページ下部の「Commit changes」をクリック
   - 変更内容の説明を入力（日本語でOK）
   - 「Commit changes」ボタンで確定

5. **サイトの更新確認**
   - 数分後にウェブサイトに反映されます

---

## ページ別更新手順

### 📰 ニュース・お知らせの追加

新しいお知らせを追加するには：

1. `_posts` フォルダを開く
2. 「Create new file」をクリック
3. ファイル名を以下の形式で入力：
   ```
   YYYY-MM-DD-タイトル.md
   例：2025-06-25-新メンバー加入のお知らせ.md
   ```

4. 以下のテンプレートをコピーして使用：
   ```markdown
   ---
   layout: post
   ---
   
   ここに本文を書きます。
   
   - 箇条書きも使えます
   - **太字**や*斜体*も可能
   
   [リンク](https://example.com)も張れます。
   ```

### 👥 メンバー情報の更新

`members.md` ファイルを編集：

```markdown
# メンバー

- 代表者: 山田 太郎（東京大学）
- メンバー: 
  - 佐藤 花子（京都大学）
  - 田中 次郎（東北大学）
  - 企業研究者: 鈴木 三郎（○○株式会社）
```

### 📄 成果物・論文の追加

`publications.md` ファイルを編集：

```markdown
# 成果物

## 論文
- 論文タイトル: 著者名, 雑誌名, 年
- [論文タイトル2](リンクURL): 著者名, 雑誌名, 年

## 報告書
- [2024年度WG活動報告書](PDFのURL)
- [技術資料集](PDFのURL)
```

### 🏠 トップページの更新

`index.md` ファイルを編集してサイトの紹介文を変更できます。

---

## ファイルの追加・削除

### 📎 報告書・PDFファイルの追加（GitHub Releases使用）

1. **リポジトリのメインページ**で右側の「Releases」をクリック
2. 「Create a new release」をクリック
3. **Tag version**: `report-YYYY-MM` などの形式で入力
4. **Release title**: 「2025年6月 活動報告書」などわかりやすいタイトル
5. **Description**: 報告書の内容説明を記入
6. **Attach binaries**: PDFファイルをドラッグ&ドロップ
7. 「Publish release」をクリック

### 🔗 GitHub Releaseのファイルにリンクする方法

アップロード後、以下の形式でリンクできます：
```markdown
[報告書名](https://github.com/ユーザー名/リポジトリ名/releases/download/タグ名/ファイル名.pdf)
```

例：
```markdown
[2024年度WG活動報告書](https://github.com/utsoraji/githubpagesdemo/releases/download/report-2024-12/report_r0.pdf)
```

### 🖼️ 画像ファイルの追加

1. `assets/images/` フォルダを開く
2. 「Upload files」をクリック
3. 画像ファイル（PNG, JPG, SVG等）をアップロード
4. 「Commit changes」で確定

### 🔗 画像ファイルへのリンク方法

画像ファイルは以下の形式でリンクできます：

```markdown
![画像の説明](assets/images/画像ファイル名.png)
```

---

## トラブルシューティング

### ❌ サイトが更新されない

**原因**: GitHub Pages の反映に時間がかかっている
**対処法**: 5-10分待ってから再度確認

### ❌ 画像が表示されない

**原因**: ファイルパスが間違っている
**対処法**: 
- ファイル名のスペルを確認
- パスが `assets/images/ファイル名` になっているか確認

### ❌ 日本語が文字化けする

**原因**: ファイルの文字エンコーディングの問題
**対処法**: GitHub の Web エディタを使用する（自動的に正しいエンコーディングになります）

---

## よくある質問

### Q: 誰でも編集できますか？
A: リポジトリの編集権限を持つメンバーのみ編集できます。権限が必要な場合は管理者にご連絡ください。

### Q: 間違って削除してしまった場合は？
A: GitHubの履歴機能で復元できます。「History」から前のバージョンを確認し、復元できます。

### Q: 複雑なレイアウトは作れますか？
A: 基本的なMarkdown記法で十分ですが、HTMLタグも使用できます。

### Q: サイトのデザインを変更できますか？
A: `assets/css/custom.css` でスタイルをカスタマイズできますが、CSSの知識が必要です。

---

## 自己解決のための情報

技術的な問題が発生した場合は、まず[トラブルシューティング](troubleshooting.md)を参照し、自己解決のための情報収集を行ってください。

---

## 技術情報（エンジニア向け）

### ローカル開発環境
[Jekyll を使用した GitHub Pages サイトのローカルテスト](https://docs.github.com/ja/pages/setting-up-a-github-pages-site-with-jekyll/testing-your-github-pages-site-locally-with-jekyll)

### カスタマイズ詳細

#### _includes/head.html
Minima テーマの head.html をカスタマイズ
- custom-head.html を読み込み

#### _layouts/home.html  
Minima テーマの home.html をカスタマイズ
- ページヘッディングの中央揃え対応
