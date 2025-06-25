# ページ管理

このページでは、サイトのページを追加・編集・削除する方法を説明します。

## Front Matter とは

### Front Matter について

<div style="background-color: #d1ecf1; padding: 15px; border-radius: 5px; margin: 15px 0;">
<strong>📋 このサイトでの設定</strong><br>
このサイトでは <code>jekyll-optional-front-matter</code> プラグインにより、通常のページでは<strong>Front Matter は不要</strong>です。各ページの最初のH1見出し（# 見出し）が自動的にページタイトルになります。
</div>

### 通常のJekyllサイトの場合（参考）

一般的なJekyllサイトでは、ページの先頭に **Front Matter** という設定情報を記載します：

```markdown
---
layout: page
title: ページタイトル
---

ここからページの内容を書きます。
```

### このサイトでの簡単な書き方

```markdown
# ページタイトル

ここからページの内容を書きます。
```

最初のH1見出しが自動的にページタイトルとして使用されます。

## ページの種類と layout

### layout: page
通常の固定ページに使用します。

```markdown
---
layout: page
title: 講座について
---

# 講座について
ここに講座の詳細を記載します。
```

**用途**: About ページ、メンバー紹介、活動概要など

### layout: post
ブログ投稿（議事録・お知らせ）に使用します。

```markdown
---
layout: post
title: 第5回会議議事録
date: 2025-06-25
---

# 第5回会議議事録
会議の内容をここに記載します。
```

**用途**: 議事録、活動報告、お知らせ

### layout: home
トップページに使用します。

```markdown
---
layout: home
title: 社会連携講座
---

# 社会連携講座へようこそ
```

## 新しいページの作成

### ステップ1: ファイル作成
1. GitHub リポジトリのメインページで「Create new file」をクリック
2. ファイル名を入力（例：`activities.md`）
3. 拡張子は必ず `.md` にする

### ステップ2: Front Matter 記述
```markdown
---
layout: page
title: 活動内容
---
```

### ステップ3: 内容記述
```markdown
# 活動内容

## 主な活動
- 定例会議（月1回）
- 研修会（四半期1回）
- 成果発表会（年2回）

## 今年度の予定
...
```

### ステップ4: 保存
1. ページ下部の「Commit new file」をクリック
2. コミットメッセージを入力（例：「活動内容ページを追加」）
3. 「Commit new file」で確定

## ファイル名とURL の関係

### 基本ルール
| ファイル名 | 生成されるURL |
|------------|---------------|
| `about.md` | `/about/` |
| `activities.md` | `/activities/` |
| `members.md` | `/members/` |

### 日本語ファイル名の注意
```markdown
# 推奨
members.md        → /members/
activities.md     → /activities/

# 非推奨（文字化けの可能性）
メンバー.md       → 文字化けする可能性
活動内容.md       → 文字化けする可能性
```

## ナビゲーションメニューへの追加

### Minima テーマでの自動メニュー
以下のファイル名は自動的にメニューに表示されます：

- `about.md` → "About"
- `contact.md` → "Contact" 

### カスタムメニューの設定
`_config.yml` でカスタムメニューを設定できます：

```yaml
header_pages:
  - about.md
  - activities.md
  - members.md
  - contact.md
```

## 既存ページの編集

### GitHub Web エディタでの編集
1. 編集したいファイル（例：`about.md`）をクリック
2. 右上の ✏️（編集アイコン）をクリック
3. 内容を修正
4. ページ下部でコミット

### 編集時の注意点
- **Front Matter** を削除しないよう注意
- **インデント**（字下げ）を正確に保つ
- **リンク切れ**がないか確認

## ページの削除

### 削除手順
1. 削除したいファイルを開く
2. 右上の 🗑️（ゴミ箱アイコン）をクリック
3. 削除理由を入力
4. 「Commit changes」で確定

### 削除前の確認事項
- 他のページからリンクされていないか
- 重要な情報が含まれていないか
- バックアップは不要か

## ページ構成のベストプラクティス

### 推奨ページ構成
```
├── index.md           (トップページ)
├── about.md           (講座について)
├── members.md         (メンバー紹介)
├── activities.md      (活動内容)
├── publications.md    (成果物・報告書)
├── contact.md         (お問い合わせ)
└── _posts/           (議事録・お知らせ)
    ├── 2025-06-25-meeting-01.md
    └── 2025-05-25-meeting-02.md
```

### 階層構造の作成
サブディレクトリを使った構成も可能です：

```
├── index.md
├── about/
│   ├── index.md       (/about/)
│   ├── history.md     (/about/history/)
│   └── purpose.md     (/about/purpose/)
└── activities/
    ├── index.md       (/activities/)
    ├── meetings.md    (/activities/meetings/)
    └── events.md      (/activities/events/)
```

## よくあるページ例

### About ページの例
```markdown
---
layout: page
title: 講座について
---

# 社会連携講座について

## 設立の背景
[背景説明]

## 目的
[目的説明]

## 活動方針
[方針説明]

## 組織体制
[体制説明]
```

### メンバー紹介ページの例
```markdown
---
layout: page
title: メンバー紹介
---

# メンバー紹介

## 責任者
**田中 太郎**（東京大学教授）
- 専門分野：社会学
- 担当：全体統括

## 副責任者
**佐藤 花子**（京都大学准教授）
- 専門分野：経済学
- 担当：研究企画

## 参加機関
- 東京大学
- 京都大学
- ○○株式会社
```

## トラブルシューティング

### Q: ページが表示されない
A: 以下を確認してください：
- Front Matter が正しく記述されているか
- ファイル拡張子が `.md` になっているか
- YAML の記法にエラーがないか

### Q: メニューに表示されない
A: `_config.yml` の `header_pages` 設定を確認してください。

### Q: リンクが機能しない
A: 相対パスでリンクを記述してください：
```markdown
[正しい](about)
[間違い](https://example.com/about)
```

---

**次のステップ**: [投稿機能](posts) で議事録・お知らせの投稿方法を学びましょう。