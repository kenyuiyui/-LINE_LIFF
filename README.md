# 語音卡片筆記 · Voice Card Notes

> 說話就能變成一張一張的文字卡片，掛在 LINE 裡的個人語音筆記小工具。
> Turn what you say into text cards — a personal voice-notes tool built as a LINE LIFF app.

🔗 **立即使用 / Try it now：** https://kenyuiyui.github.io/-LINE_LIFF/
（需先加官方帳號好友 / Requires adding the official account as a friend first）

---

## 這是什麼 / What is this

**語音卡片筆記**幫忙記筆記卡關的人（開會靈感一直冒但打字跟不上、上課想用講的代替抄寫）解決「講得比打字快，但講完就忘記重點」的問題，不用再事後回想、事後補打逐字稿。

打開工具、按下錄音，你講的話會被即時轉成一張一張的文字卡片，講完可以合併句子、調整順序、修改內容，最後一鍵送回 LINE 聊天室或分享出去。多人接力錄音（例如一人錄上半場、另一人錄下半場）或多組人各自開會的內容，也可以透過共用的 Google Sheet 互相查看、混合勾選、一起生成整合摘要。

**Voice Card Notes** helps people who think faster than they type — in a meeting, in class, or just walking around with an idea — turn spoken words into organized text cards, without needing to transcribe everything by hand afterward.

Open it, hit record, and your speech turns into cards as you talk. Merge sentences, reorder them, edit the text, then send the result straight back to a LINE chat or share it elsewhere. When multiple people take turns recording (e.g. one person records the first half, another the second) or multiple groups each keep their own notes, a shared Google Sheet lets everyone browse, mix, and select each other's content together for a combined AI summary.

---

## 為什麼做這個 / Why I built this

我自己常常在討論或會議中靈感一直冒出來，但打字速度完全跟不上講話速度，等討論結束想整理重點，腦袋已經一片空白，只記得「好像講了什麼很棒的點子」卻想不起細節。

市面上語音轉文字的工具不少，但我想要一個**輕量、不用額外下載 App、打開 LINE 就能用**的版本——剛好我自己也常用 LINE 跟朋友、同學互動，順手就做了這個掛在 LIFF 裡的小工具。

因為只是個人維護、業餘時間做的小工具，功能上比較陽春，也還在持續調整；但基本的「講話 → 變成卡片 → 整理 → 送出」這個核心流程，我自己每天在用，算是做得順手。

I kept running into the same problem: ideas come faster than I can type, especially during discussions. By the time a conversation ends, I'd remember that something great was said — just not what, exactly.

There are plenty of voice-to-text tools out there, but I wanted something **lightweight that didn't require installing a separate app** — something that just worked inside LINE, since that's where I already talk to friends and classmates. So I built this as a LIFF app.

This is a personal project built in my spare time, so it's not polished or feature-rich — but the core loop (speak → get cards → organize → send) is something I genuinely use every day.

---

## 介面架構 / Interface layout

工具分成 5 個分頁，同一時間只顯示一個分頁的內容：

| 分頁 | 內容 |
|---|---|
| 🎙️ **錄音** | 即時錄音轉文字、上傳既有語音檔案 |
| 🗂️ **筆記** | 語音卡片列表，含合併／調順序／編輯／勾選四種操作模式，以及發送（送回聊天室、分享出去） |
| 📖 **共享** | 讀取共用 Google Sheet、勾選要查看或納入摘要的資料 |
| 📝 **摘要** | AI 摘要生成，混合「筆記」與「共享」兩邊勾選的內容 |
| ⚙️ **設定** | Groq／Gemini API Key、逐項資料刪除、一次清除全部本機資料 |

API Key 輸入區固定在「設定」分頁，不會佔用其他分頁的版面；若對應 Key 還沒設定，「錄音」與「摘要」分頁會顯示一條精簡提示，點一下就能直接跳去設定分頁填寫。

The tool is organized into 5 tabs, showing one panel at a time:

| Tab | Content |
|---|---|
| 🎙️ **Record** | Live transcription and audio file upload |
| 🗂️ **Notes** | The card list, with merge / reorder / edit / select modes, plus sending (back to chat, or share out) |
| 📖 **Shared** | Load a shared Google Sheet and pick entries to view or include in a summary |
| 📝 **Summary** | Generate an AI summary, mixing selections from both Notes and Shared |
| ⚙️ **Settings** | Groq/Gemini API keys, per-item data deletion, and a full local-data wipe |

API keys live entirely on the Settings tab and don't take up space elsewhere; if a required key is missing, the Record or Summary tab shows a short prompt that jumps straight to Settings.

---

## 功能 / Features

- 🎙️ 即時錄音，講話同時卡片陸續生成，不用等整段錄完（每 15 秒自動切一段送出轉寫）
- 📁 上傳既有語音檔案轉文字，適合長輩傳來的 LINE 語音訊息或既有錄音檔
- ✏️ 卡片編輯模式：合併句子、調整順序、修改內容、勾選納入摘要
- 📖 **讀取共享 Google Sheet 筆記**（唯讀）：貼上共用表格連結，勾選多筆資料查看，或混合自己的語音卡片一起送去生成摘要
- 🔢 **自訂勾選順序**：送去 AI 生成摘要的順序＝使用者勾選的先後順序，不是固定依表格排列，每個勾選項目旁會顯示順序編號
- 🏷️ **類型標記**：共享表格裡的資料分為「🎤 逐字稿」與「📝 摘要」兩種類型並用顏色區分，避免不小心把別人的摘要當成逐字稿疊加使用
- 🧠 一鍵生成 AI 摘要（需自行設定 Gemini API Key，選填功能），可將摘要結果複製、分享，或存回共用 Sheet 供其他人查看
- 📋 一鍵「複製成 Sheet 貼上格式」：把卡片或摘要內容打包成一整包資料，貼到 Google Sheet 任一空白儲存格即可，複製前可自訂主題名稱
- 📥 三種發送方式：送回 LINE 聊天室、分享給 LINE 好友、分享到其他 App；內容較長時自動分批送出，分享中途取消也能在下次接續，不用整段重來
- 🔒 自動儲存草稿在本機，誤觸返回或切出頁面也不怕內容消失
- 🧹 逐項刪除本機資料（API Key、卡片草稿、摘要等各自獨立管理），也可一次清除全部
- 🌏 內建簡轉繁保險，避免語音辨識偶爾跳出簡體字

<br>

- 🎙️ Live transcription — cards appear as you speak, no need to wait until you're done (auto-segments every 15 seconds)
- 📁 Upload an existing audio file for transcription — handy for LINE voice messages or pre-recorded audio
- ✏️ Card editing modes: merge sentences, reorder, edit text, or select cards for summarization
- 📖 **Read shared Google Sheet notes** (read-only): paste a shared spreadsheet link, select multiple entries, and optionally mix them with your own voice cards for a combined summary
- 🔢 **Custom selection order**: the order sent to the AI for summarization follows the order you selected items in — not a fixed sheet order — with an order badge shown next to each selected item
- 🏷️ **Type tagging**: shared-sheet entries are labeled as either "🎤 Transcript" or "📝 Summary" with distinct colors, so you don't accidentally stack someone else's summary into another summarization pass
- 🧠 One-tap AI summary generation (optional, requires your own Gemini API Key); copy, share, or save the result back to the shared sheet for others to see
- 📋 One-tap "Copy as Sheet paste format": packages cards or a summary into a single blob you paste into any empty Google Sheet cell, with an optional custom topic name prompt before copying
- 📥 Three ways to send: back to the LINE chat, to a LINE friend, or to another app; long content auto-splits into batches, and an interrupted share can be resumed next time instead of starting over
- 🔒 Drafts auto-save locally, so accidental navigation won't wipe your notes
- 🧹 Delete local data item by item (API keys, card drafts, summaries, etc. each managed independently), or wipe everything at once
- 🌏 Built-in Simplified-to-Traditional Chinese conversion as a safety net

---

## 關於「共享筆記」與「AI 摘要」/ About Shared Notes & AI Summary

這兩個功能是為了「多人接力錄音、或多方人馬各自整理、事後想合併對照重點」的情境設計的——例如一人錄上半場、另一人錄下半場；或兩組人各自開會，事後想整合成一份總覽。

**運作方式：**

1. 每個人各自在「筆記」分頁把整理好的卡片內容，用「複製成 Sheet 貼上格式」按鈕複製（複製前會詢問一個主題名稱，例如「上半場逐字稿」），貼到同一份共用 Google Sheet 的下一個空白儲存格
2. 任何人打開這個工具，在「共享」分頁貼上該 Sheet 的分享連結並讀取
3. 讀取成功後，在清單裡勾選想查看或想納入摘要的資料，可複選、可跨欄位混搭，勾選順序即為之後送去生成摘要的順序
4. 切到「摘要」分頁，還可以額外勾選自己「筆記」分頁裡的語音卡片一起加入，混合來源生成同一份摘要
5. 生成好的摘要可以用「存回 Sheet」按鈕，同樣複製成一整包資料貼回共用表格，讓其他人也能讀到（會被標記為「摘要」類型，跟原始逐字稿區分開來）

**資料格式：**

這份共用 Google Sheet 從此不是設計給人類直接閱讀的表格，而是純粹的資料庫——每一格（A1、A2、A3...）都存放一整包 JSON 資料，格式為：

```json
{"label": "上半場逐字稿", "content": "...", "timestamp": "2026-09-03 14:00", "type": "raw"}
```

`type` 為 `raw`（逐字稿）或 `summary`（摘要）。人類使用者只需要負責「複製、貼上」，不需要理解或手動維護任何欄位對應關係，格式的產生與解析都交給工具處理。

**重要限制：**

- **只能讀取，不會寫入**——把內容加進 Sheet 完全是手動複製貼上的操作，這個工具不會自動幫你寫進去
- 對方的 Google Sheet 需要設定為「知道連結的使用者可檢視」，否則讀不到
- 只讀取第一個工作分頁
- 多人同時手動貼上時沒有鎖定機制，建議貼上前先確認自己要貼在空白儲存格，避免覆蓋別人的資料
- 請不要手動編輯儲存格內容或自行輸入格式，一律使用「複製成 Sheet 貼上格式」／「存回 Sheet」按鈕產生的內容直接貼上；若某幾筆格式有問題，讀取時會清楚標示、略過那幾筆，其餘資料仍正常顯示

These two features are for situations where multiple people take turns recording, or multiple groups each keep their own notes and want to combine them afterward — e.g. one person records the first half of a session and another records the second half, or two teams in separate meetings who want to merge their takeaways.

**How it works:**

1. Everyone copies their organized cards from the Notes tab using "Copy as Sheet paste format" (you'll be prompted for a topic name, e.g. "First half transcript"), and pastes it into the next empty cell of the same shared Google Sheet
2. Anyone can open this tool, paste the Sheet's share link on the Shared tab, and load it
3. Once loaded, select the entries you want to view or include in a summary — multi-select is supported, and the order you click them in becomes the order used for summarization
4. On the Summary tab, you can additionally select your own voice cards from the Notes tab to mix in, combining sources into a single summary
5. A generated summary can be copied back to the shared sheet via "Save to Sheet," tagged as a `summary` type so others can tell it apart from raw transcripts

**Data format:**

This shared Google Sheet is no longer meant to be read directly by humans — it's a pure data store. Each cell (A1, A2, A3...) holds one complete JSON blob:

```json
{"label": "First half transcript", "content": "...", "timestamp": "2026-09-03 14:00", "type": "raw"}
```

`type` is either `raw` (transcript) or `summary`. Humans only need to copy and paste — no need to understand or maintain any column mapping; formatting and parsing are handled entirely by the tool.

**Important limitations:**

- **Read-only** — adding content to the Sheet is entirely manual; this tool never writes to it automatically
- The Google Sheet must be set to "Anyone with the link can view," or it won't load
- Only the first worksheet tab is read
- There's no locking mechanism for simultaneous manual pasting — please double-check you're pasting into an empty cell to avoid overwriting someone else's data
- Please don't hand-edit cell contents or type in your own format — always paste content produced by the "Copy as Sheet paste format" / "Save to Sheet" buttons; if a few entries are malformed, they'll be clearly flagged and skipped on load without affecting the rest

---

## 使用前請知道 / Before you use it

這是個人開發、非商用的免費小工具，使用前想誠實讓你知道：

- 需要自行申請免費的 [Groq API Key](https://console.groq.com/keys)（設定分頁內有申請教學，約兩分鐘、免信用卡）
- 你的語音內容**會上傳到 Groq 雲端伺服器**進行轉寫，原始音檔不會保留，僅保留轉出來的文字
- 若使用 AI 摘要功能，逐字稿內容**會上傳到 Google Gemini 雲端伺服器**進行摘要生成（需自行申請 Gemini API Key，屬選填功能）
- 若使用「共享」分頁的功能，你貼上的 Sheet 連結會用來向 **Google 文件伺服器**發出讀取請求
- Groq／Gemini Key 與整理好的卡片、摘要內容，會存在**你自己這台裝置的瀏覽器裡**；若為共用裝置，可在「設定」分頁逐項刪除，或一次清除全部本機資料
- **不建議**用來記錄真正機密或高度敏感的內容（商業機密、他人個資、密碼、身分證字號等）
- 這是個人維護的小工具，**沒有正式客服或服務保證**，可能因故調整或中止服務
- 使用前工具會請你先詳閱一份使用須知並同意，才能開始使用

This is a free, personally-maintained tool — not a commercial product. A few things worth knowing upfront:

- You'll need your own free [Groq API Key](https://console.groq.com/keys) (a short guide is built into the Settings tab, no credit card required)
- Your voice **is uploaded to Groq's servers** for transcription; the raw audio is discarded afterward, only the transcribed text is kept
- If you use the AI summary feature, your transcript **is uploaded to Google Gemini's servers** for summarization (requires your own optional Gemini API Key)
- If you use the Shared tab, the Sheet link you paste is used to send a read request to **Google's document servers**
- Your Groq/Gemini keys and saved cards/summaries live in **your own device's browser storage**; on a shared device, you can delete items individually or wipe everything at once from the Settings tab
- **Not recommended** for sensitive content (business secrets, personal data of others, passwords, ID numbers, etc.)
- This is a personal side project with **no formal support guarantee** and may change or be discontinued
- You'll be asked to read and agree to a short usage notice before first use

---

## 技術架構 / Tech stack

純前端 LINE LIFF 應用，單一 HTML 檔案，無後端伺服器：

- **LIFF SDK**：好友身份驗證、登入、傳送訊息、分享目標選擇
- **MediaRecorder API**：瀏覽器端錄音
- **Groq Whisper API**（`whisper-large-v3-turbo`）：語音轉文字
- **Google Gemini API**：AI 摘要生成（選填功能）
- **Google Sheets CSV 匯出端點**：讀取共享筆記表格，每格內容為 JSON，搭配自製的簡易 CSV parser（處理雙引號跳脫、逗號、換行）
- **opencc-js**：簡體轉繁體轉換
- **localStorage**：API Key、卡片草稿、摘要、分享中斷續傳記錄的本機持久化
- **Content-Security-Policy**：限制外部資源來源，並對關鍵 CDN 資源加上 SRI 完整性驗證

A pure front-end LINE LIFF app, single HTML file, no backend server:

- **LIFF SDK** for friendship verification, login, message sending, and share target picker
- **MediaRecorder API** for in-browser audio recording
- **Groq Whisper API** (`whisper-large-v3-turbo`) for transcription
- **Google Gemini API** for AI summary generation (optional)
- **Google Sheets CSV export endpoint** for reading shared notes, where each cell holds a JSON blob, paired with a hand-written CSV parser (handles quoted-field escaping, commas, and line breaks)
- **opencc-js** for Simplified-to-Traditional Chinese conversion
- **localStorage** for persisting API keys, card drafts, summaries, and share-resume state locally
- **Content-Security-Policy**, with Subresource Integrity (SRI) on key CDN assets

---

## 回報問題 / Reporting issues

如果你在使用時遇到問題、發現安全性漏洞，或有功能建議，歡迎透過以下方式讓我知道：

1. 前往這個 repo 的 [Issues 頁面](../../issues)，看看是不是已經有人回報過類似狀況
2. 沒有的話，開一個新的 Issue，盡量附上：
   - 你在做什麼操作時發生的（例如「按下送回聊天室之後」）
   - 預期結果 vs. 實際結果
   - 使用的裝置與瀏覽器（例如 iPhone Safari、Android Chrome）
   - 如果方便，附上截圖
3. 如果是**安全性問題**，也可以透過官方帳號私下回報，不用公開在 Issue 裡描述細節

這是個人維護的小工具，沒辦法保證多快回覆或修復，但每一則回報我都會看，謝謝你的耐心與幫忙。

If you run into a bug, find a security issue, or have a feature suggestion, here's how to reach me:

1. Check the [Issues page](../../issues) to see if it's already been reported
2. If not, open a new Issue with as much of the following as you can:
   - What you were doing when it happened (e.g. "after tapping Send to Chat")
   - Expected vs. actual behavior
   - Device and browser (e.g. iPhone Safari, Android Chrome)
   - A screenshot, if possible
3. For **security issues**, feel free to report privately via the official LINE account instead of posting details publicly

This is a personal project maintained in my spare time, so I can't promise a fast turnaround — but I do read every report. Thanks for your patience and help.

---

## 授權 / License

本專案採用 [MIT License](./LICENSE) 授權。簡單來說：你可以自由使用、複製、修改、散布這份程式碼，包含商業用途，唯一的要求是保留原始的版權聲明與授權條款。程式碼「按現狀提供」，不附帶任何擔保。

This project is licensed under the [MIT License](./LICENSE). In short: you're free to use, copy, modify, and distribute this code — including for commercial purposes — as long as you keep the original copyright notice and license text. The code is provided "as is," without warranty of any kind.
