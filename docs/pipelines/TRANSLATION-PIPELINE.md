# Translation Pipeline — 英文翻譯流程

> 目前暫停（Cron disabled）。Issue #229 追蹤英文品質問題。
> 重啟前需先設計 v2 翻譯品質標準。

---

## 現況

- 英文 479 篇 > 中文 420 篇（量已超越，但品質落後）
- 大部分英文版是 v1 機翻，未經人工審核
- Issue #229：英文文章停留在舊版翻譯，需大幅更新

---

## 流程（v1，已暫停）

```
git pull → 找待翻譯文章 → 重寫式翻譯（3篇/批）→ 更新 _translations.json → build → push
```

### Step 1：找待翻譯文章

```bash
cd ~/taiwan-md
# 中文文章
find knowledge/ -maxdepth 2 -name '*.md' ! -path '*/en/*' ! -path '*/about/*' ! -name '_*' | sort > /tmp/zh-articles.txt
# 已有英文版
find knowledge/en/ -name '*.md' ! -name '_*' | sort > /tmp/en-articles.txt
# 映射表
cat knowledge/_translations.json | head -20
```

### Step 2：翻譯（重寫式，非逐字翻）

對每篇：

1. 讀取中文原文
2. **重寫式翻譯**——讀起來像英文母語者寫的策展文章
3. 台灣專有名詞保留中文 + 英文解釋
4. 文化脈絡不熟悉的概念加簡短解釋
5. 保留 frontmatter 格式，翻譯 title/description
6. 保持策展人聲音——有觀點、有溫度
7. 長度可比原文稍長（文化解釋），不超過 120%
8. 保留所有參考資料 URL
9. 「📝 策展人筆記」「⚠️ 爭議觀點」等 emoji 保留，文字翻譯
10. 存到 `knowledge/en/{Category}/{english-slug}.md`

### Step 3：更新映射 + Push

```bash
cd ~/taiwan-md
# 更新 _translations.json
git add knowledge/en/ knowledge/_translations.json
git commit -m "feat(en): translate X articles — [分類]"
git push
```

---

## ⚠️ 鐵律

### 翻譯 ≠ 逐句翻

逐句翻出來的英文讀起來像 Google Translate。好的英文版 = 為外國讀者重新組織的文章。

### 台灣主權立場

- ❌ 不把台灣描述為中國的一部分
- ✅ 使用 "Indigenous peoples" 而非 "aborigines"
- ✅ 台灣專有名詞用中文 + 英文解釋（如 "night market (夜市)"）

### 不要 git add -A

只 add `knowledge/en/` 和 `_translations.json`。

### 每批最多 3 篇

控制品質。一次翻太多 = 每篇都草率。

### 優先序

Food > Culture > History > Nature > Art > Technology > Economy > Music > Society > Geography > Lifestyle > People

（People 最後，因為人物文章翻譯需要更多文化背景知識）

---

## 待改善（v2 設計中）

1. **翻譯品質分級**：v1（機翻）→ v2（結構化翻譯）→ v3（文化轉譯）
2. **先翻高流量頁**：用 GA4 數據排序，不是按分類順序
3. **中英文 revision 差距偵測**：中文 revision 5 但英文還是 revision 1 → 需更新
4. **翻譯 quality-scan**：英文版也需要品質掃描

---

## 相關檔案

| 檔案                            | 用途                 |
| ------------------------------- | -------------------- |
| `knowledge/en/`                 | 英文文章目錄         |
| `knowledge/_translations.json`  | 中英文映射表         |
| `EDITORIAL.md`                  | 品質標準（中英通用） |
| `docs/editorial/TERMINOLOGY.md` | 用語標準             |

## 相關 Cron

| Cron                     | 狀態        | 說明                      |
| ------------------------ | ----------- | ------------------------- |
| taiwan-md-en-translation | ❌ disabled | 每小時 3 篇，品質不足暫停 |

## 相關 Issue

- #229：英文文章需大幅更新

---

_版本：v1.0 | 2026-03-29_
_狀態：暫停中，等 v2 設計_
