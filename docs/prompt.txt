請幫我做一個「15 秒的動畫解說網頁」，主題是「什麼是 AI agent」。

【輸出】
只輸出「一個完整的 HTML 檔」，放在一個程式碼區塊裡。CSS 和 JavaScript 都寫在同一個檔案，不要分成多個檔案。可以用 Artifact 或 Canvas 預覽的話，請直接預覽。

【工具】
- 動畫用 Anime.js 3.2.2：<script src="https://cdnjs.cloudflare.com/ajax/libs/animejs/3.2.2/anime.min.js"></script>
- 字型用 Google Fonts 的 Noto Sans TC（400 和 900），後面接系統字型：
  font-family: "Noto Sans TC", "PingFang TC", "Microsoft JhengHei", sans-serif;
- 不要用 import、模組或其他外部檔案，雙擊 .html 檔就要能播。

【版面】
- body 黑底、置中，裡面一個 16:9 的 #stage：
  width: min(100vw, 177.78vh); height: min(56.25vw, 100vh); position: relative; overflow: hidden; 背景深藍 #0B1E3F。
- 四個場景都是 #stage 裡的 <section class="scene">，每個都寫：
  position: absolute; inset: 0; display: flex; flex-direction: column; align-items: center; justify-content: center; opacity: 0;
- 白字，重點色鴨黃 #FFC93C。字級用 vmin，最大的字不超過 9vmin，畫面不能有字超出。

【四個場景，總長 15 秒】
第 1 段（0–3 秒）：大標「什麼是 AI agent？」彈出，下方小字「15 秒看懂」淡入。
第 2 段（3–7 秒）：左右兩張卡依序滑入。左卡「聊天機器人」＋「你問，它答」；右卡「AI agent」＋「你交代，它去做」，右卡用鴨黃邊框。卡片寬 40vmin，文字不換行（white-space: nowrap）。
第 3 段（7–12 秒）：三個圓圈從左到右依序亮起，中間有箭頭「→」。圓圈直徑 20vmin，圈裡只寫一個大字「看」「想」「做」，圈下方寫小字「讀資料」「排步驟」「用工具」。還沒亮是半透明灰圈，亮起時背景變鴨黃、字變深藍。三個都亮起後，底下出現一行「做完再看結果，不對就再來一輪」。
第 4 段（12–15 秒）：結尾大字「你給目標，它跑流程」，下方小字「藍鴨 Launchdock Lab」。

【動畫寫法】
- 用一條 anime.timeline()，每一步都用第二個參數寫開始時間（毫秒），例如 tl.add({ targets: '#s2', opacity: [0, 1], duration: 400 }, 3000)。
- 每個場景播完要把它的 opacity 調回 0，下一個場景才出現，同一時間只看得到一個場景。
- 帶單位的值一定要加引號，例如 translateY: ['3vmin', 0]、translateX: ['-50vw', 0]。
- 不要用 offset 屬性，不要用 duration: 0（最短寫 1），場景切換只改 opacity，不要用 display:none 或 visibility:hidden。
- 網頁一打開就自動播。
- 如果 Anime.js 沒載到（typeof anime === 'undefined'），就把所有場景直接顯示出來，畫面不能空白。

【再播一次】
- #stage 右下角放一個 <button>「▶ 再播一次」</button>，一開始看不到（opacity: 0; pointer-events: none）。
- 播完停在最後一個畫面，按鈕才出現。按了先把所有元素恢復原狀（清掉 inline style），再從頭播。

【寫完自己檢查】
第 1.5、5、10、14 秒時，畫面上只看得到該段的字，而且都在畫面中間；任何時候都不能整片空白。
