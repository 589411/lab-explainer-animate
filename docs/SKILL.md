---
name: animated-explainer
description: 把一個主題做成 15 秒、四個場景的中文動畫解說網頁（單一 HTML 檔，用 Anime.js），附「再播一次」按鈕。使用者說「做一個動畫解說」「把這個主題做成 15 秒動畫」「做動畫網頁」時使用。
---

# 15 秒動畫解說網頁

## 先問清楚（缺的才問，最多一題）
- 主題是什麼？只給主題就自己寫四段內容：開場標題、對比或定義、三個步驟、一句結尾。
- 沒說的就用預設：深藍底 #0B1E3F、白字、重點色鴨黃 #FFC93C。

## 輸出規則
1. 只輸出一個完整的 HTML 檔，放在一個程式碼區塊裡。CSS、JavaScript 都寫在同一個檔案，不用 import、不用模組。
   能用「Artifact」或「Canvas」預覽就用，讓使用者直接看到動畫。
2. 動畫用 Anime.js 3.2.2：
   `<script src="https://cdnjs.cloudflare.com/ajax/libs/animejs/3.2.2/anime.min.js"></script>`
   - 用 `anime.timeline()`，每一步用第二個參數寫開始時間（毫秒），例如 `tl.add({...}, 3000)`。
   - 不要用 `offset` 屬性，不要用 `duration: 0`（最短 1）。
   - Anime.js 沒載到時，直接顯示所有文字，畫面不能空白。
3. 字型：Google Fonts 的 Noto Sans TC（400、900），後接 `"PingFang TC", "Microsoft JhengHei", sans-serif`。
4. 版面：整個視窗是 16:9 置中的動畫區。字級用 vw 或 vmin，手機和電腦都不能超出畫面。每行最多 16 個中文字。
5. 時間：四個場景依序播放，總長 15 秒（3 秒、4 秒、5 秒、3 秒）。一打開就自動播。場景切換只改 opacity，不要用 display:none 或 visibility:hidden。
6. 播完停在最後一個畫面，右下角出現「▶ 再播一次」，按了先把所有元素恢復原狀再從頭播。
7. 寫完自己檢查：第 1.5、5、10、14 秒畫面上看得到哪些字，要和四段內容一致，任何時候都不能整片空白。

## 回覆格式
先給程式碼區塊，再用兩句話告訴使用者：
- 「直接在右邊預覽看動畫；或把程式碼存成 animation.html，雙擊用瀏覽器打開。」
- 「想要影片檔，可以用螢幕錄影錄下來（Mac 按 ⌘⇧5，Windows 按 Win+Alt+R）。」
