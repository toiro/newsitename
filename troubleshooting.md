# トラブルシューティング

このページでは、GitHub Pages + Jekyll サイト運用でよく発生する問題と解決方法を説明します。

## 緊急時の対応手順

### 🚨 サイト全体が表示されない場合

#### 症状
- サイトにアクセスしても何も表示されない
- 「404 Page not found」エラー
- 「Site not found」エラー

#### 確認手順
1. **GitHub Pages の設定確認**
   - Settings → Pages で設定が有効か
   - Source が「Deploy from a branch」になっているか
   - Branch が「main」になっているか

2. **_config.yml の確認**
   - YAML 記法にエラーがないか
   - インデント（字下げ）が正しいか

#### 解決方法
```yaml
# _config.yml の最小構成に戻す
title: サイト名
theme: minima
markdown: CommonMarkGhPages
```

### 🔧 ページの一部が表示されない場合

#### 症状
- 特定のページでエラー
- 画像が表示されない
- リンクが機能しない

#### 診断手順
1. **個別ページの確認**
   - ファイル名の確認
   - パスの確認
   - 記法エラーの確認

2. **段階的な切り分け**
   - 問題のある部分を特定
   - 最小構成でテスト

## よくある問題と解決法

### Jekyll ビルドエラー

#### Error: YAML Exception
```
YAML Exception reading /_config.yml: 
syntax error on line 15, column 28
```

**原因**: YAML の記法エラー

**解決法**:
```yaml
# 間違った例
title: サイト名
description: これは
  複数行の説明です  # エラー

# 正しい例
title: サイト名
description: >
  これは
  複数行の説明です
```

#### Error: Liquid Exception
```
Liquid Exception: Liquid syntax error
```

**原因**: Markdown 内の特殊文字

**解決法**:
```markdown
<!-- 間違った例 -->
価格は {{ price }} 円です

<!-- 正しい例 -->
価格は {% raw %}{{ price }}{% endraw %} 円です
```

### CommonMarkGhPages 特有の問題

#### 表が正しく表示されない
```markdown
# 間違った例（パイプの位置がずれている）
| 項目|内容 |
|-----|--- |
|日時|2025年6月25日|

# 正しい例
| 項目 | 内容 |
|------|------|
| 日時 | 2025年6月25日 |
```

#### 脚注が機能しない
```markdown
# 間違った例
重要な情報です[^1]
[^1]: 脚注の内容

# 正しい例（空行が必要）
重要な情報です[^1]

[^1]: 脚注の内容
```

### Minima テーマでの表示問題

#### ナビゲーションメニューに表示されない

**原因**: header_pages の設定不備

**解決法**:
```yaml
# _config.yml に追加
header_pages:
  - about.md
  - members.md
  - activities.md
```

#### フォントが正しく表示されない

**原因**: CSS の競合または文字エンコーディング

**解決法**:
1. **GitHub Web エディタ**を使用して編集
2. **UTF-8** エンコーディングを確認
3. **ブラウザキャッシュ**をクリア

## ファイル関連の問題

### 画像が表示されない

#### 確認項目
| チェック項目 | 確認方法 |
|-------------|----------|
| **ファイルパス** | `assets/images/filename.png` |
| **ファイル名** | 大文字小文字の正確性 |
| **ファイル形式** | .png, .jpg, .gif, .svg |
| **ファイルサイズ** | 1MB 以下推奨 |

#### 解決手順
1. **ファイルの存在確認**
   ```markdown
   ![テスト画像](assets/images/test.png)
   ```

2. **パスの修正**
   ```markdown
   # 相対パス（推奨）
   ![画像](assets/images/image.png)
   
   # 絶対パス（避ける）
   ![画像](/assets/images/image.png)
   ```

### PDFリンクが機能しない

#### GitHub Releases のURL確認
```markdown
# 正しいURL形式
https://github.com/[username]/[repository]/releases/download/[tag]/[filename.pdf]

# 例
https://github.com/university/social-cooperation/releases/download/report-2025-06/monthly-report.pdf
```

#### よくある間違い
```markdown
# 間違い：Releases ページのURL
https://github.com/user/repo/releases/tag/report-2025-06

# 正しい：ダウンロードURL
https://github.com/user/repo/releases/download/report-2025-06/file.pdf
```

## 投稿（Posts）の問題

### 投稿が表示されない

#### ファイル名の確認
```bash
# 正しい形式
2025-06-25-meeting-minutes.md

# 間違った形式
meeting-minutes.md           # 日付なし
2025-6-25-meeting.md        # 0埋めなし
2025-06-25 meeting.md       # スペース含む
```

#### Front Matter の確認
```markdown
---
layout: post
---
```

### 投稿の日付順が正しくない

**原因**: ファイル名の日付形式の間違い

**解決法**: ファイル名の日付形式を正確に
```bash
# 正しいファイル名
2025-06-25-post.md

# 間違った例
2025-6-25-post.md     # 月日の0埋めなし
25-06-2025-post.md    # 日付順序が違う
```

## パフォーマンスの問題

### サイトの読み込みが遅い

#### 画像の最適化
```markdown
# 推奨サイズ
- Web表示用: 500KB 以下
- 写真: 2MB 以下
- 図表: 200KB 以下
```

#### ファイル数の最適化
```markdown
# 不要ファイルの削除
- 古い画像ファイル
- 未使用のPDF
- テスト用ファイル
```

### GitHub Pages のビルド時間が長い

**原因**: 大量のファイルまたは大容量ファイル

**解決法**:
```yaml
# _config.yml に除外設定を追加
exclude:
  - vendor/
  - node_modules/
  - "*.psd"
  - "*.ai"
```

## セキュリティとプライバシー

### 機密情報の誤掲載

#### 即座の対応
1. **該当ファイルの削除**
2. **履歴からの削除**（上級者向け）
3. **関係者への通知**

#### 予防策
```markdown
# 掲載前のチェックリスト
- [ ] 個人情報の確認
- [ ] 内部資料でないか
- [ ] 公開範囲は適切か
- [ ] 著作権の問題はないか
```

### アクセス権限の管理

#### Collaborators の確認
1. **Settings** → **Manage access**
2. **不要なアクセス権の削除**
3. **最小権限の原則**を適用

## 復旧作業

### ファイルの復元

#### GitHub 履歴からの復元
1. **該当ファイルを開く**
2. **History** タブをクリック
3. **復元したいバージョン**を選択
4. **Raw** でコンテンツをコピー
5. **新しいファイルとして保存**

#### 全体の復元
```bash
# Git を使った復元（上級者向け）
git revert HEAD
git push origin main
```

### サイト全体のリセット

#### 最終手段（データ消失注意）
1. **リポジトリの削除**
2. **テンプレートからの再作成**
3. **バックアップからの復元**


---

**参考資料**: [テンプレート集](templates) で関連情報を確認できます。