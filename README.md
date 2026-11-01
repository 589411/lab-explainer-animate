# ✨ 免安裝：一段文字做動畫解說

**你不用會寫程式，也不用安裝任何東西。** 只要會用瀏覽器，把一段文字貼給網頁版 AI（Claude、ChatGPT 或 Gemini），它就會做出一段 15 秒的動畫解說。

👉 看成品、一步步教學、複製文字，都在這裡：**https://animate.launchdock.app**

這是[藍鴨 AI 實例庫](https://lab.launchdock.app)的一張卡片。想直接做出 MP4 影片，請看進階版：[一句話做解說影片](https://explainer.launchdock.app)。

## 1. 先看成品
[`reference/ai-agent.html`](reference/ai-agent.html)：下載後雙擊就能用瀏覽器播放。
這是「網頁動畫」，不是影片檔（MP4）。想要影片檔，用螢幕錄影錄下來（Mac 按 ⌘⇧5；Windows 11 用「剪取工具」的錄製）。

## 2. 照著做
1. **打開一個網頁版 AI：** [claude.ai](https://claude.ai)、[chatgpt.com](https://chatgpt.com) 或 [gemini.google.com](https://gemini.google.com)。用 Gemini 的話，先在輸入框下方點「Canvas」（畫布，可以直接預覽網頁的功能）。
2. **貼上文字：** 把 [`prompt.md`](prompt.md) 整段複製，貼進輸入框，按送出。
3. **等它寫：** 大約 30 秒到 2 分鐘，會跑出一大段程式碼，看不懂沒關係。
4. **看動畫：** Claude 會在右邊的「Artifact」（成品視窗）直接播；ChatGPT 和 Gemini 在 Canvas 右上角按「預覽」。
5. **沒有預覽：** 把程式碼存成 `animation.html`，雙擊打開。
6. **畫面怪怪的：** 回它一句「畫面空白（或：字疊在一起），請修好，再給我完整的 HTML。」
7. **換主題：** 把「什麼是 AI agent」和四段內容換掉，再貼一次。

## 3. 進階：存成固定的小幫手
「技能」（skill）是一份給 AI 看的說明書，存起來以後只要說主題。
- **Claude：** 設定 → 功能，打開「程式碼執行與建立檔案」；再到「自訂 → 技能」上傳 [`docs/animated-explainer.zip`](docs/animated-explainer.zip)（內容就是 [`skill/animated-explainer/SKILL.md`](skill/animated-explainer/SKILL.md)）。
- **ChatGPT：** 個人帳號目前不能上傳技能。改用「專案」（Projects），把 [`instructions.txt`](instructions.txt) 貼進專案的「指示」。
- **Gemini：** 新增一個 Gem（自訂小幫手），把 [`instructions.txt`](instructions.txt) 貼進「指示」。

## 資料夾
| 路徑 | 內容 |
|---|---|
| `docs/` | 展示頁（GitHub Pages 從這裡發布） |
| `prompt.md` | 要複製的那段文字 |
| `instructions.txt` | 給 ChatGPT 專案／Gemini Gem 的指示 |
| `skill/animated-explainer/SKILL.md` | 技能檔 |
| `reference/ai-agent.html` | 範例動畫 |

## 授權
見 [LICENSE.md](LICENSE.md)。Anime.js 是 MIT 授權；字型 Noto Sans TC 是 OFL 授權，都可以免費商用。
