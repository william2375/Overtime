# 薪資計算機｜iOS PWA 部署套件

## 檔案
- `index.html`：原薪資與加班費計算機，保留既有功能及本機資料儲存。
- `manifest.json`：PWA 名稱、啟動方式與圖示設定。
- `service-worker.js`：快取主頁與已成功載入的 CDN 資源，提供基本離線啟動能力。
- `icons/`：iOS 與 PWA 圖示。

## Netlify 部署
1. 解壓縮 ZIP。
2. 開啟 https://app.netlify.com/drop 。
3. 將解壓後的 `薪資計算機_PWA` 資料夾整個拖曳上傳（確認 `index.html` 位於部署根目錄）。
4. 等待 Netlify 產生 HTTPS 網址。
5. 在 iPhone 使用 Safari 開啟該網址，點「分享」→「加入主畫面」，名稱使用「薪資計算機」。
6. 若顯示「以網頁 App 方式打開」選項，請開啟後再新增。

## 注意事項
- 薪資與出勤資料仍使用瀏覽器 `localStorage`，儲存在該 iPhone／該網站來源的本機環境。清除 Safari 網站資料、改用不同網域或不同瀏覽器，可能無法讀取原資料。建議定期使用程式內的 JSON 備份功能。
- 行事曆更新 API 需要網路；Service Worker 刻意不快取行事曆 API，避免手動更新時拿到過期資料。
- Tailwind、Chart.js、SheetJS、Lucide 與 Google Fonts 使用外部 CDN。首次成功載入後，Service Worker 會嘗試快取已請求的資源；因此離線能力取決於這些資源是否曾成功載入並被瀏覽器快取。
- 這是可安裝的 PWA 網頁 App，不是原生 iOS App，也不會上架 App Store。
