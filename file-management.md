# ファイル・資料管理

このページでは、PDFファイル、画像、その他の資料を効果的に管理する方法を説明します。

## ファイル管理の基本方針

### 社会連携講座での推奨構成
```
├── assets/
│   └── images/          # 画像ファイル
│       ├── logos/       # ロゴ・アイコン
│       ├── diagrams/    # 図表・グラフ
│       └── photos/      # 写真
└── GitHub Releases      # PDF・報告書
```

### ファイル種別ごとの管理方法
| ファイル種別 | 管理場所 | 用途 |
|-------------|----------|------|
| **画像** (.png, .jpg, .svg) | `assets/images/` | ページ内表示 |
| **PDF** (.pdf) | GitHub Releases | ダウンロード配布 |
| **Office文書** (.docx, .xlsx) | GitHub Releases | ダウンロード配布 |

## 画像ファイルの管理

### 画像アップロード手順

#### ステップ1: assets/images フォルダにアクセス
1. GitHub リポジトリで **assets** → **images** フォルダを開く
2. 「Upload files」をクリック

#### ステップ2: ファイルアップロード
1. 画像ファイルをドラッグ&ドロップ
2. または「choose your files」で選択
3. 複数ファイルの同時アップロード可能

#### ステップ3: コミット
1. コミットメッセージを入力（例：「会議資料の図表を追加」）
2. 「Commit changes」をクリック

### 推奨画像形式
| 形式 | 用途 | 特徴 |
|------|------|------|
| **PNG** | 図表・スクリーンショット | 高画質、透明背景対応 |
| **JPG** | 写真 | ファイルサイズ小 |
| **SVG** | ロゴ・アイコン | 拡大縮小で劣化しない |

### 画像ファイル名の付け方
```bash
# 良い例
logo-university.png
diagram-project-structure.png
photo-seminar-20250625.jpg

# 避けるべき例
画像1.png                    # 日本語
IMG_001.jpg                  # 意味不明
very long file name.png      # スペース含む
```

### ページでの画像表示

#### 基本的な表示
```markdown
![画像の説明](assets/images/diagram-project.png)
```

#### サイズ指定（HTML使用）
```markdown
<img src="assets/images/logo.png" alt="ロゴ" width="200">
```

#### 中央揃え表示
```markdown
<div style="text-align: center;">
<img src="assets/images/diagram.png" alt="組織図" width="400">
</div>
```

## GitHub Releases でのPDF管理

### GitHub Releases とは
- **バージョン管理**されたファイル配布システム
- **大容量ファイル**に対応
- **ダウンロード統計**取得可能
- **永続的なURL**でアクセス可能

### PDF アップロード手順

#### ステップ1: Releases ページにアクセス
1. リポジトリのメインページで右側の「Releases」をクリック
2. 「Create a new release」をクリック

#### ステップ2: リリース情報入力
```
Tag version: report-2025-06
Release title: 2025年6月 活動報告書
Description: 
第1四半期の活動報告書です。
- 会議議事録まとめ
- 予算執行状況
- 今後の予定
```

#### ステップ3: ファイル添付
1. 「Attach binaries by dropping them here or selecting them.」エリアにPDFをドラッグ
2. 複数ファイルの同時アップロード可能
3. アップロード完了を確認

#### ステップ4: 公開
1. 「Publish release」をクリック
2. 自動的に URL が生成される

### Tag名の付け方（重要）

#### Tag名の基本原則
**Tag名は後から変更できません**し、**リポジトリ内で重複できません**。慎重に決めましょう。

<div style="background-color: #fff3cd; padding: 15px; border-radius: 5px; margin: 15px 0;">
<strong>⚠️ 重要な制約</strong><br>
• <strong>ユニーク制約</strong>: 同じリポジトリ内で同じTag名は使用不可<br>
• <strong>変更不可</strong>: 一度作成したTag名は後から変更できない<br>
• <strong>削除困難</strong>: Tagの削除は可能だが、既存リンクが切れる
</div>

| 原則 | 説明 | 例 |
|------|------|-----|
| **英数字のみ** | 日本語不可、スペース不可 | ❌ `報告書 2025` → ⭕ `report-2025` |
| **小文字推奨** | 統一性のため | ❌ `Report-2025` → ⭕ `report-2025` |
| **ハイフン区切り** | 読みやすさのため | ❌ `report2025june` → ⭕ `report-2025-06` |
| **時系列順序** | 並び替えを考慮 | ❌ `june-2025` → ⭕ `2025-06` |

#### 社会連携講座向けTag名テンプレート

##### 📊 定期報告書
```bash
# 月次報告書
monthly-2025-01    # 2025年1月分
monthly-2025-02    # 2025年2月分

# 四半期報告書  
quarterly-2025-q1  # 2025年第1四半期
quarterly-2025-q2  # 2025年第2四半期

# 年次報告書
annual-2024        # 2024年度
annual-2025        # 2025年度
```

##### 📝 会議資料
```bash
# 定例会議資料
meeting-2025-01-15    # 2025年1月15日の会議
meeting-2025-02-20    # 2025年2月20日の会議

# 臨時会議
emergency-2025-03-10  # 2025年3月10日の緊急会議

# 議事録まとめ
minutes-2025-q1       # 2025年第1四半期議事録集
```

##### 📋 規則・ガイドライン
```bash
# バージョン管理が必要な文書
guidelines-v1.0       # ガイドライン初版
guidelines-v1.1       # ガイドライン改訂版
guidelines-v2.0       # ガイドライン大幅改訂

# 規程・規則
regulations-2025      # 2025年版規程
manual-v3.0          # マニュアル第3版
```

##### 🎯 イベント・研修資料
```bash
# セミナー・研修
seminar-2025-spring   # 2025年春季セミナー
training-basic-v1     # 基礎研修教材
workshop-2025-06-15   # 2025年6月15日ワークショップ
```

#### よくある間違いと正しい例

| ❌ 間違い | 理由 | ⭕ 正しい例 |
|-----------|------|------------|
| `2025年6月報告書` | 日本語・スペース | `monthly-2025-06` |
| `Report_June_2025` | アンダースコア | `report-2025-06` |
| `june-2025-report` | 時系列が逆 | `report-2025-06` |
| `REPORT-2025-06` | 大文字 | `report-2025-06` |
| `report-2025-6` | ゼロ埋めなし | `report-2025-06` |
| `report-2025-06` | 既存Tag名と重複 | `meeting-2025-06` |

#### ユニーク制約で困るケース

**問題**: 同じ月に複数の資料をアップロードしたい
```bash
# ❌ これは重複エラーになる
monthly-2025-06    # 月次報告書
monthly-2025-06    # 別の資料（同じTag名で作成不可）
```

**解決策**: 用途を明確に区分する
```bash
# ⭕ 用途別に明確化
monthly-report-2025-06    # 月次報告書
monthly-minutes-2025-06   # 月次議事録
monthly-budget-2025-06    # 月次予算資料
```

#### Tag名の決定フローチャート

```
📋 どんな資料？
├── 定期報告書 → 種類-YYYY-MM または 種類-YYYY-QX
├── 会議資料 → meeting-YYYY-MM-DD
├── ガイドライン → 文書名-vX.Y
└── イベント資料 → イベント種類-YYYY-MM-DD
```

#### 命名のベストプラクティス

##### 1. **一貫性を保つ**
```bash
# 良い例：形式が統一されている
monthly-2025-01
monthly-2025-02
monthly-2025-03

# 悪い例：形式がバラバラ
january-2025
report-feb-2025
2025-march-monthly
```

##### 2. **将来を考慮する**
```bash
# 良い例：拡張性がある
report-2025-01        # 月次以外も追加可能
annual-report-2025    # 年次報告書として明確

# 悪い例：拡張しにくい
jan-report            # 年が不明
first-report          # 順序が不明確
```

##### 3. **検索しやすくする**
```bash
# 良い例：プレフィックスで分類
meeting-2025-01-15
meeting-2025-02-20
report-2025-01
report-2025-02

# 悪い例：分類が困難
20250115-meeting
january-report-2025
```

#### Release title の例
Release title は日本語でわかりやすく記述できます。

```
2025年6月 活動報告書
2025年度 年次報告書  
第1四半期 議事録集
研究ガイドライン v1.0
緊急会議資料（予算関連）
春季セミナー 配布資料
```

#### Tag名とRelease titleの関係

| Tag名（英数字のみ） | Release title（日本語OK） |
|-------------------|------------------------|
| `monthly-2025-06` | `2025年6月 月次活動報告書` |
| `annual-2024` | `2024年度 年次報告書` |
| `guidelines-v2.0` | `活動ガイドライン 第2版` |
| `emergency-2025-03-10` | `緊急会議資料（予算審議）` |

#### 実際の例：Tag名決定プロセス

**ケース1: 2025年4月の月次報告書**
```
❓ 何の資料？ → 月次報告書
❓ いつの？ → 2025年4月  
❓ Tag名 → monthly-2025-04
❓ Title → 2025年4月 月次活動報告書
```

**ケース2: 緊急理事会の議事録**
```
❓ 何の資料？ → 会議議事録（緊急）
❓ いつの？ → 2025年3月15日
❓ Tag名 → emergency-2025-03-15
❓ Title → 緊急理事会議事録（予算承認）
```

**ケース3: 研修マニュアルの改訂版**
```
❓ 何の資料？ → 研修マニュアル
❓ バージョン？ → 第2版
❓ Tag名 → training-manual-v2.0
❓ Title → 新人研修マニュアル 第2版
```

### ページからのリンク方法

#### 基本的なリンク
```markdown
[報告書ダウンロード](https://github.com/username/repository/releases/download/report-2025-06/activity-report.pdf)
```

#### リンク一覧表の例
```markdown
## 報告書一覧

| 期間 | タイトル | ダウンロード |
|------|----------|-------------|
| 2025年6月 | 第1四半期活動報告 | [PDF](https://github.com/user/repo/releases/download/report-2025-06/q1-report.pdf) |
| 2025年3月 | 年度末総括報告 | [PDF](https://github.com/user/repo/releases/download/annual-2024/annual-report.pdf) |
```

## ファイル整理のベストプラクティス

### フォルダ構成例
```
assets/
└── images/
    ├── logos/
    │   ├── university-logo.png
    │   └── project-logo.svg
    ├── diagrams/
    │   ├── organization-chart.png
    │   ├── project-timeline.png
    │   └── budget-breakdown.png
    ├── photos/
    │   ├── seminar-20250625.jpg
    │   ├── meeting-room.jpg
    │   └── team-photo-2025.jpg
    └── screenshots/
        ├── system-interface.png
        └── data-dashboard.png
```

### ファイル命名の統一ルール

#### 日付の表記
```
# ISO 8601 形式を推奨
YYYY-MM-DD-description.ext
2025-06-25-meeting-photo.jpg
2025-06-25-budget-chart.png
```

#### 内容による分類
```
# 種別-内容-日付.拡張子
diagram-organization-2025.png
photo-seminar-20250625.jpg
chart-budget-q1.png
logo-university-main.svg
```

## 外部ファイルの埋め込み

### PDF ビューワーの埋め込み
```markdown
<iframe src="https://github.com/user/repo/releases/download/tag/file.pdf" 
        width="100%" height="600px">
</iframe>
```

### Google Drive ファイルの埋め込み
```markdown
<iframe src="https://drive.google.com/file/d/FILE_ID/preview" 
        width="100%" height="480">
</iframe>
```

## ファイルサイズとパフォーマンス

### 推奨ファイルサイズ
| ファイル種別 | 推奨サイズ | 最大サイズ |
|-------------|-----------|-----------|
| **Web表示画像** | < 500KB | < 1MB |
| **PDF（Releases）** | < 10MB | < 25MB |
| **写真** | < 2MB | < 5MB |

### 画像最適化のコツ
1. **解像度調整**: Web表示は 72-96 DPI で十分
2. **圧縮**: PNG は 8bit、JPG は 80% 品質
3. **形式選択**: 写真は JPG、図表は PNG

## アクセス制御とセキュリティ

### パブリックリポジトリでの注意点
- すべてのファイルが **公開** される
- 機密情報は **絶対にアップロードしない**
- 個人情報の取り扱いに注意

### 機密ファイルの管理
```markdown
# 機密度の高いファイルの場合
- プライベートリポジトリを使用
- または外部の限定公開サービスを利用
- パスワード保護PDFの使用を検討
```

## トラブルシューティング

### Q: 画像が表示されない
A: 以下を確認してください：
- ファイルパスが正しいか
- ファイル名の大文字小文字
- 画像形式が対応しているか

### Q: PDFダウンロードリンクが機能しない
A: GitHub Releases の URL 形式を確認：
```
https://github.com/[username]/[repository]/releases/download/[tag]/[filename]
```

### Q: ファイルアップロードができない
A: 以下を確認：
- ファイルサイズが制限内か
- ネットワーク接続は正常か
- ブラウザを変更してみる

## ファイル管理の定期メンテナンス

### 月次チェック項目
- [ ] 不要ファイルの削除
- [ ] ファイル名の統一性確認
- [ ] リンク切れチェック
- [ ] ストレージ使用量確認

### 年次整理作業
- [ ] 古いファイルのアーカイブ
- [ ] フォルダ構成の見直し
- [ ] 命名規則の更新
- [ ] バックアップ状況確認

---

**次のステップ**: [日常運用](update-operations) で日々の更新作業について学びましょう。