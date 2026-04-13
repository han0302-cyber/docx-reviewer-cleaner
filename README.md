# DOCX 檢閱者名稱整理 / DOCX Reviewer Name Cleaner / DOCX 校閲者名の整理

批次改寫 Word 追蹤修訂（Track Changes）中的檢閱者名稱。**純瀏覽器客戶端**處理，檔案不會上傳到任何伺服器，適合處理內部或機敏文件。介面支援**繁體中文 / English / 日本語**三種語言，右上角可隨時切換。

## 功能

- 解析 `.docx` 內所有追蹤修訂的作者（`w:author`）與數量
- 自訂每位檢閱者要改寫成的新名稱
- 同步更新對應的 `w:initials` 縮寫
- 輸出新的 `.docx` 檔案，原檔不動

## 使用方式

### 直接開啟

```bash
git clone https://github.com/han0302-cyber/docx-reviewer-cleaner.git
cd docx-reviewer-cleaner
```

然後雙擊 `index.html`，或用瀏覽器打開即可。不需要安裝任何東西、不需要啟動 server。

### 操作流程

1. 拖曳或點擊選擇一份含追蹤修訂的 `.docx`
2. 頁面會列出所有檢閱者與修訂筆數
3. 在「新名稱」欄輸入想改寫成的名字（留白代表保留原名）
4. 按「套用並下載」取得新檔案 `原檔名_renamed.docx`

## 技術細節

- 單一 `index.html` + 本地 vendored 的 `jszip.min.js`，無任何建置步驟
- 使用 [JSZip v3.10.1](https://stuk.github.io/jszip/)（MIT 授權）負責 `.docx` 的解壓與重組
- `.docx` 內部是 ZIP + XML，工具會掃描所有 `.xml` 成員，用正則替換 `w:author` 與 `w:initials` 屬性
- 檔案完全在瀏覽器記憶體中處理，不經任何後端
- 100% 離線可用，不依賴任何 CDN 或網路連線

## 授權

本專案以 [MIT License](./LICENSE) 釋出。

本專案同時內含第三方開源元件（JSZip），其授權資訊請見 [THIRD_PARTY_LICENSES.md](./THIRD_PARTY_LICENSES.md)。
