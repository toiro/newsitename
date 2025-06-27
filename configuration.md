# _config.yml 設定詳細

このページでは、Jekyll サイトの中核となる設定ファイル `_config.yml` について詳しく説明します。

## _config.yml とは

### 設定ファイルの役割
`_config.yml` は Jekyll サイトの **基本設定を管理するファイル** です。サイト全体の動作を制御します。

### 重要な特徴
- **YAML 形式**で記述
- **サイト全体**に影響
- 変更後は **サイトの再構築** が必要
- **インデント（字下げ）**が重要

## 基本設定項目

### サイト情報
```yaml
title: 社会連携講座の活動報告サイト
author: 田中 太郎
email: contact@example.com
description: >
  社会連携講座の活動状況、議事録、
  報告書を共有するためのサイトです。

baseurl: ""           # サブディレクトリがある場合のみ
url: "https://username.github.io"
```

### 各項目の説明
| 項目 | 説明 | 例 |
|------|------|-----|
| `title` | サイトのタイトル | `社会連携講座` |
| `author` | サイト作成者 | `田中 太郎` |
| `email` | 連絡先メールアドレス | `info@example.com` |
| `description` | サイトの説明 | `活動報告サイト` |
| `baseurl` | サブディレクトリ | 通常は空 |
| `url` | サイトのURL | GitHub Pages のURL |

## テーマとマークダウン設定

### 現在の推奨設定
```yaml
theme: minima
markdown: CommonMarkGhPages

commonmark:
  options: ["UNSAFE", "SMART", "FOOTNOTES"]
  extensions: ["strikethrough", "autolink", "table", "tagfilter"]
```

### 設定項目の詳細

#### theme: minima
- **Minima テーマ**を使用
- シンプルで読みやすいデザイン
- GitHub Pages で標準サポート

#### markdown: CommonMarkGhPages
- **CommonMark 仕様**準拠
- GitHub Pages 最適化
- 標準 Markdown より多機能

#### commonmark options
| オプション | 説明 |
|-----------|------|
| `UNSAFE` | HTML タグの混在を許可（注意: セキュリティリスクあり） |
| `SMART` | 引用符・ダッシュの自動変換 |
| `FOOTNOTES` | 脚注機能を有効化 |

#### commonmark extensions
| 拡張機能 | 説明 |
|---------|------|
| `strikethrough` | ~~取り消し線~~ |
| `autolink` | URL の自動リンク化 |
| `table` | テーブル（表）の作成 |
| `tagfilter` | 危険な HTML タグをフィルタ |

## プラグイン設定

### 推奨プラグイン構成
```yaml
plugins:
  - jekyll-feed
  # - jekyll-titles-from-headings  # GitHub Pages では制限あり

# titles_from_headings:
#   strip_title: true
#   collections: false
```

### プラグインの説明

#### jekyll-feed
- **RSS フィード**を自動生成
- ブログ投稿の更新情報を配信
- `/feed.xml` でアクセス可能

#### jekyll-titles-from-headings
- **見出し**から自動的にページタイトルを生成
- Front Matter で title を省略可能
- `strip_title: true` でタイトル重複を防止

## Minima テーマ専用設定

### ソーシャルメディア設定
```yaml
minima:
  social_links:
    - { platform: github, user_url: "https://github.com/username" }
    - { platform: email, user_url: "mailto:contact@example.com" }
```

### ヘッダーページの設定
```yaml
header_pages:
  - about.md
  - members.md
  - activities.md
  - publications.md
  - contact.md
```

#### header_pages の詳細
- **サイトのナビゲーションメニュー**に表示するページを指定
- **配列形式**でファイル名を列挙
- **表示順序**は記載順に従う
- **Front Matter**で `title` を設定しないページは、最初の見出しがタイトルになる

#### 実際の例（このサイトの設定）
```yaml
header_pages:
  - about-system.md          # GitHub Pages + Jekyll とは
  - setup.md                 # サイト作成の準備
  - commonmark-guide.md      # CommonMark 記法
  - page-management.md       # ページ管理
  - posts.md                 # 投稿機能
  - file-management.md       # ファイル・資料管理
  - update-operations.md     # 更新作業
  - templates.md             # テンプレート
  - configuration.md         # _config.yml 設定詳細
  - minima-customization.md  # Minima テーマカスタマイズ
  - troubleshooting.md       # トラブルシューティング
```

#### header_pages を設定しない場合
`header_pages` を設定しない（コメントアウトまたは削除）すると：
- **自動的に**ルートディレクトリの `.md` ファイルがナビゲーションに表示される
- **アルファベット順**で並び替えられる
- **index.md** は除外される

```yaml
# header_pages を設定しない場合の例
# header_pages:
#   - about.md
#   - contact.md
```

この場合、以下のような自動表示になります：
```
about.md → About
contact.md → Contact  
help.md → Help
members.md → Members
```

#### 注意事項
- ファイル名は**拡張子 `.md` も含めて**記載する
- 存在しないファイルを指定するとリンクエラーになる
- ページを増やす場合は、この設定も合わせて更新する
- **表示順序を制御したい場合**は `header_pages` の設定が必須

### Google Analytics 設定
```yaml
google_analytics: G-XXXXXXXXXX  # Google Analytics ID
```

## 高度な設定

### 除外ファイル設定
```yaml
exclude:
  - Gemfile
  - Gemfile.lock
  - node_modules
  - vendor/
  - .sass-cache/
  - .jekyll-cache/
  - gemfiles/
```

### コレクション設定（上級者向け）
```yaml
collections:
  reports:
    output: true
    permalink: /:collection/:name/
```

### デフォルト設定
```yaml
defaults:
  - scope:
      path: ""
      type: "posts"
    values:
      layout: "post"
      author: "社会連携講座事務局"
  - scope:
      path: ""
      type: "pages"
    values:
      layout: "page"
```

## 社会連携講座向け完全設定例

### 推奨 _config.yml
```yaml
# サイト設定
title: 社会連携講座活動報告サイト
author: 社会連携講座事務局
email: social-cooperation@university.ac.jp
description: >
  大学と企業の連携による社会課題解決を目指す
  社会連携講座の活動報告、議事録、成果物を
  共有するためのサイトです。

baseurl: ""
url: "https://university.github.io"

# テーマ・マークダウン設定
theme: minima
markdown: CommonMarkGhPages

commonmark:
  options: ["UNSAFE", "SMART", "FOOTNOTES"]
  extensions: ["strikethrough", "autolink", "table", "tagfilter"]

# プラグイン
plugins:
  - jekyll-feed
  - jekyll-titles-from-headings

titles_from_headings:
  strip_title: true
  collections: false

# Minima テーマ設定
minima:
  social_links:
    - { platform: email, user_url: "mailto:social-cooperation@university.ac.jp" }
    - { platform: github, user_url: "https://github.com/university/social-cooperation" }

# ナビゲーションメニュー
header_pages:
  - about.md
  - members.md
  - activities.md
  - publications.md
  - contact.md

# 除外ファイル
exclude:
  - Gemfile
  - README.md

# デフォルト設定
defaults:
  - scope:
      path: ""
      type: "posts"
    values:
      layout: "post"
      author: "事務局"
  - scope:
      path: ""
      type: "pages"
    values:
      layout: "page"
```

## 設定変更時の注意点

### YAML 記法の重要ポイント

#### インデント（字下げ）
```yaml
# 正しい例
commonmark:
  options: ["UNSAFE", "SMART"]
  extensions: ["table"]

# 間違った例（インデントが不統一）
commonmark:
options: ["UNSAFE", "SMART"]
   extensions: ["table"]
```

#### 文字列の扱い
```yaml
# 通常の文字列
title: 社会連携講座

# 複数行の文字列
description: >
  これは複数行にわたる
  説明文です。

# 特殊文字を含む場合
email: "test+tag@example.com"
```

### 設定変更後の確認手順
1. **変更をコミット**
2. **5-10分待機**（GitHub Pages の再構築）
3. **サイトの動作確認**
4. **エラーがある場合は設定を見直し**

## トラブルシューティング

### よくあるエラー

#### YAML 構文エラー
```
Error: YAML Exception reading /_config.yml: 
syntax error on line XX
```

**解決法**: インデントと記法を確認

#### プラグインエラー
```
Error: The plugin 'jekyll-xxx' could not be found
```

**解決法**: Gemfile に必要なプラグインを追加

#### テーマエラー
```
Error: The theme 'minima' could not be found
```

**解決法**: GitHub Pages サポート対象テーマか確認

### 設定の検証方法

#### 最小構成でのテスト
```yaml
# エラー箇所特定のための最小設定
title: テストサイト
theme: minima
markdown: CommonMarkGhPages
```

#### 段階的な設定追加
1. 基本設定のみでテスト
2. プラグインを段階的に追加
3. 各段階で動作確認

## 定期メンテナンス

### 月次チェック項目
- [ ] サイト情報の更新確認
- [ ] 連絡先情報の確認
- [ ] プラグインの動作確認

### 年次見直し項目
- [ ] Jekyll バージョンの確認
- [ ] 新機能の検討
- [ ] セキュリティ設定の見直し

---

**次のステップ**: [日常運用](update-operations) で日々の更新作業について学びましょう。