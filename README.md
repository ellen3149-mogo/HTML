# 新北市預售屋實價登錄 — Google Sites 部署說明

## 📁 檔案清單

| 檔案 | 說明 | 大小 |
|------|------|------|
| `data.json` | 所有交易資料（44,979 筆） | ~11 MB |
| `widget-1-search.html` | 搜尋篩選 + 資料清單 | ~17 KB |
| `widget-2-charts.html` | 統計圖表分析 | ~10 KB |
| `widget-3-calculator.html` | 價格計算器 | ~14 KB |

---

## 🚀 步驟一：將資料上傳至 GitHub Pages

### 1. 建立 GitHub Repository

1. 登入 [github.com](https://github.com)
2. 點擊右上角 **+** → **New repository**
3. Repository name 填入：`realestate-data`（或任意名稱）
4. 選 **Public**（必須是 Public，才能公開存取 raw 檔案）
5. 勾選 **Add a README file**
6. 點擊 **Create repository**

### 2. 上傳 data.json

1. 進入剛建立的 repo 頁面
2. 點擊 **Add file** → **Upload files**
3. 將 `data.json` 拖曳上傳
4. 點擊 **Commit changes**

### 3. 取得 Raw URL

上傳完成後，點擊 `data.json` 檔案，再點右上角 **Raw** 按鈕，複製網址，格式如下：

```
https://raw.githubusercontent.com/YOUR_USERNAME/realestate-data/main/data.json
```

---

## ✏️ 步驟二：修改三個 Widget 的 DATA_URL

用文字編輯器（記事本、VSCode 等）開啟每個 widget HTML 檔，找到這一行：

```javascript
const DATA_URL = 'https://raw.githubusercontent.com/YOUR_USERNAME/YOUR_REPO/main/data.json';
```

將 `YOUR_USERNAME` 和 `YOUR_REPO` 替換成您的 GitHub 帳號和 repo 名稱。

**三個檔案都要修改。**

---

## 🌐 步驟三：將 Widget 嵌入 Google Sites

每個 widget 都要分別嵌入。以下以 Widget 1 為例：

1. 開啟您的 **Google Sites** 編輯頁面
2. 點擊要插入的位置
3. 右側工具列點擊 **嵌入** (Embed)
4. 選擇 **嵌入程式碼** (Embed code)
5. 開啟 `widget-1-search.html`，全選內容（Ctrl+A）複製
6. 貼入 Google Sites 的嵌入框
7. 點擊 **下一步** → **插入**
8. 調整區塊大小（建議高度：搜尋器 700px 以上）

重複以上步驟，分別插入 widget-2 和 widget-3。

---

## 📐 建議的 Google Sites 版面配置

```
[標題區] 新北市預售屋實價登錄查詢系統

[全寬區塊] widget-1-search.html   ← 搜尋篩選（建議高度 750px）

[分欄區塊 or 全寬] widget-2-charts.html  ← 統計分析（建議高度 900px）

[全寬區塊] widget-3-calculator.html  ← 計算器（建議高度 600px）
```

---

## ⚠️ 常見問題

**Q: 資料載入失敗（紅色錯誤訊息）**
- 確認 GitHub repo 是 **Public**
- 確認 DATA_URL 路徑正確（注意大小寫）
- 瀏覽器可能需要允許 CORS；GitHub raw 檔案預設允許

**Q: Google Sites 嵌入後看不到內容**
- Google Sites 嵌入區塊需要手動拉大高度
- 部分學校/企業的 Google Workspace 管理員可能有限制嵌入，請洽 IT 管理員

**Q: 資料多久更新一次？**
- 只要重新上傳 `data.json` 到 GitHub，Widget 下次載入即會取得新資料

