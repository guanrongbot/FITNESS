# FitLog Firebase 個人雲端版

已設定 Firebase 專案 `fitness-58145`，匿名登入，Firestore 存在 `users/{uid}/state/main`。

## 發布（電腦上一次）

1. 安裝 Node.js 與 Firebase CLI：`npm install -g firebase-tools`
2. 解壓本 ZIP，開啟此資料夾的終端機。
3. `firebase login` （登入你自己的 Google 帳號）
4. `firebase deploy --only hosting --project fitness-58145`
5. 成功後，手機打開 Firebase CLI 回傳的 Hosting URL（一般為 https://fitness-58145.web.app），再加入主畫面。

安全規則：請確認 Firebase Console > Firestore Database > Rules 已使用本專案的 `firestore.rules` 內容。請勿使用公開讀寫規則。

## 重要注意

- 使用匿名登入，不需要按登入，但匿名身分綁定目前瀏覽器。**換手機或清除瀏覽器資料可能無法取回舊資料**；定期用網頁「匯出 JSON 備份」。
- 網頁會把資料自動同步 Firestore，並保留 localStorage 暫存。雲端失敗會在網頁頂部顯示錯誤，不應認為已上傳。
- 單一使用者操作設計；**不同手機分別匿名登入不會共用紀錄**。
- 本版本沒有直接 AI 照片辨識，仍可把 ChatGPT 產生的餐點 JSON 貼入匯入。
- 首次使用如果手機瀏覽器內存有舊版 LocalStorage 紀錄且雲端空白，將上傳這些紀錄；若雲端已有紀錄，以雲端資料為準。
- 不要直接從 iPhone「檔案」打開 HTML：要使用 Hosting HTTPS 網址。
- Firebase web `apiKey` 是前端識別設定，不是管理員密鑰；仍必須使用安全規則。

如果 Firebase Console 的 Firestore 資料庫不是「(default)」，需修改前端 getFirestore 設定以指定正確資料庫 ID。


注意：這是另一個 Firebase 專案，舊專案中的匿名使用者和資料不會自動搬到此專案。請先在 fitness-58145 啟用 Authentication → Anonymous、建立 Firestore Database（預設資料庫），並發布 firestore.rules。若使用 GitHub Pages，將 public/index.html 放進 GitHub Pages 服務的正確入口。
