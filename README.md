# 語音卡片筆記 · Voice Card Notes

> 說話就能變成一張一張的文字卡片，掛在 LINE 裡的個人語音筆記小工具。
> Turn what you say into text cards — a personal voice-notes tool built as a LINE LIFF app.

🔗 **立即使用 / Try it now：** https://kenyuiyui.github.io/-LINE_LIFF/
（需先加官方帳號好友 / Requires adding the official account as a friend first）

---

## 這是什麼 / What is this

**語音卡片筆記**幫忙記筆記卡關的人（開會靈感一直冒但打字跟不上、上課想用講的代替抄寫）解決「講得比打字快，但講完就忘記重點」的問題，不用再事後回想、事後補打逐字稿。

打開工具、按下錄音，你講的話會被即時轉成一張一張的文字卡片，講完可以合併句子、調整順序、修改內容，最後一鍵送回 LINE 聊天室或分享出去。多人各自開會、各自整理的內容，也可以透過共用的 Google Sheet 互相查看彼此的筆記。

**Voice Card Notes** helps people who think faster than they type — in a meeting, in class, or just walking around with an idea — turn spoken words into organized text cards, without needing to transcribe everything by hand afterward.

Open it, hit record, and your speech turns into cards as you talk. Merge sentences, reorder them, edit the text, then send the result straight back to a LINE chat or share it elsewhere. If multiple groups are each taking their own notes, a shared Google Sheet lets everyone browse each other's notes too.

---

## 為什麼做這個 / Why I built this

我自己常常在討論或會議中靈感一直冒出來，但打字速度完全跟不上講話速度，等討論結束想整理重點，腦袋已經一片空白，只記得「好像講了什麼很棒的點子」卻想不起細節。

市面上語音轉文字的工具不少，但我想要一個**輕量、不用額外下載 App、打開 LINE 就能用**的版本——剛好我自己也常用 LINE 跟朋友、同學互動，順手就做了這個掛在 LIFF 裡的小工具。

因為只是個人維護、業餘時間做的小工具，功能上比較陽春，也還在持續調整；但基本的「講話 → 變成卡片 → 整理 → 送出」這個核心流程，我自己每天在用，算是做得順手。

I kept running into the same problem: ideas come faster than I can type, especially during discussions. By the time a conversation ends, I'd remember that something great was said — just not what, exactly.

There are plenty of voice-to-text tools out there, but I wanted something **lightweight that didn't require installing a separate app** — something that just worked inside LINE, since that's where I already talk to friends and classmates. So I built this as a LIFF app.

This is a personal project built in my spare time, so it's not polished or feature-rich — but the core loop (speak → get cards → organize → send) is something I genuinely use every day.

---

## 功能 / Features

- 🎙️ 即時錄音，講話同時卡片陸續生成，不用等整段錄完（每 15 秒自動切一段送出轉寫）
- 📁 上傳既有語音檔案轉文字，適合長輩傳來的 LINE 語音訊息或既有錄音檔
- 🧠 一鍵生成會議摘要（需自行設定 Gemini API Key，選填功能）
- ✏️ 卡片編輯模式：合併句子、調整順序、修改內容
- 📖 **查看共享 Google Sheet 筆記**（唯讀）：貼上共用表格連結，用下拉選單挑選要看誰整理的內容，適合多方各自開會、事後互相查看彼此筆記的情境
- 📋 一鍵「複製成 Sheet 貼上格式」：把目前卡片內容組成可直接貼進 Google Sheet 儲存格的格式，貼上時自動分欄，不用手動拆
- 📥 三種發送方式：送回 LINE 聊天室、分享給 LINE 好友、分享到其他 App
- 🔒 自動儲存草稿在本機，誤觸返回或切出頁面也不怕內容消失
- 🧹 一鍵清除本機資料，方便共用裝置使用後清乾淨
- 🌏 內建簡轉繁保險，避免語音辨識偶爾跳出簡體字

<br>

- 🎙️ Live transcription — cards appear as you speak, no need to wait until you're done (auto-segments every 15 seconds)
- 📁 Upload an existing audio file for transcription — handy for LINE voice messages or pre-recorded audio
- 🧠 One-tap meeting summary generation (optional, requires your own Gemini API Key)
- ✏️ Card editing modes: merge sentences, reorder, edit text
- 📖 **View shared Google Sheet notes** (read-only): paste a shared spreadsheet link and pick whose notes to view from a dropdown — great for when multiple groups each keep their own notes and want to browse each other's afterward
- 📋 One-tap "Copy as Sheet paste format": formats your current cards into text you can paste directly into a Google Sheet cell, auto-splitting into columns on paste
- 📥 Three ways to send: back to the LINE chat, to a LINE friend, or to another app
- 🔒 Drafts auto-save locally, so accidental navigation won't wipe your notes
- 🧹 One-tap local data clear, useful on shared devices
- 🌏 Built-in Simplified-to-Traditional Chinese conversion as a safety net

---

## 關於「查看共享筆記」/ About "Shared Notes"

這個功能是為了「多方人馬各自錄音整理、想互相看到彼此內容」的情境設計的，例如兩組人各自開會，事後想合併對照重點。

**運作方式：**

1. 大家各自把整理好的卡片內容，用工具內建的「複製成 Sheet 貼上格式」按鈕複製，貼到同一份共用 Google Sheet 的空白列（A 欄=標籤、B 欄=內容、C 欄=時間，第一列保留當標題列）
2. 任何人打開這個工具，在「查看共享筆記」區塊貼上該 Sheet 的分享連結
3. 讀取成功後，用下拉選單選擇想看的那一筆，內容會以唯讀方式顯示

**重要限制：**

- **只能讀取，不會寫入**——把內容加進 Sheet 完全是手動操作，這個工具不會自動幫你寫進去
- 對方的 Google Sheet 需要設定為「知道連結的使用者可檢視」，否則讀不到
- 只讀取第一個工作分頁
- 多人同時手動貼上時沒有鎖定機制，建議貼上前先確認自己要貼在空白列，避免覆蓋別人的資料

This feature is for situations where multiple groups each keep their own voice notes and want to browse each other's afterward — for example, two teams in separate meetings who want to compare notes later.

**How it works:**

1. Everyone copies their organized cards using the built-in "Copy as Sheet paste format" button, and pastes it into an empty row of the same shared Google Sheet (column A = label, B = content, C = timestamp; row 1 is reserved as the header)
2. Anyone can open this tool, paste the Sheet's share link into the "Shared Notes" section
3. Once loaded, pick an entry from the dropdown to view its content (read-only)

**Important limitations:**

- **Read-only** — adding content to the Sheet is entirely manual; this tool never writes to it automatically
- The Google Sheet must be set to "Anyone with the link can view", or it won't load
- Only the first worksheet tab is read
- There's no locking mechanism for simultaneous manual pasting — please double-check you're pasting into an empty row to avoid overwriting someone else's data

---

## 使用前請知道 / Before you use it

這是個人開發、非商用的免費小工具，使用前想誠實讓你知道：

- 需要自行申請免費的 [Groq API Key](https://console.groq.com/keys)（工具內有申請教學，約兩分鐘、免信用卡）
- 你的語音內容**會上傳到 Groq 雲端伺服器**進行轉寫，原始音檔不會保留，僅保留轉出來的文字
- 若使用會議摘要功能，逐字稿內容**會上傳到 Google Gemini 雲端伺服器**進行摘要生成（需自行申請 Gemini API Key，屬選填功能）
- 若使用「查看共享筆記」功能，你貼上的 Sheet 連結會用來向 **Google 文件伺服器**發出讀取請求
- Groq／Gemini Key 與整理好的卡片、摘要內容，會存在**你自己這台裝置的瀏覽器裡**；若為共用裝置，請於使用後點選工具內的「清除本機資料」
- **不建議**用來記錄真正機密或高度敏感的內容（商業機密、他人個資、密碼、身分證字號等）
- 這是個人維護的小工具，**沒有正式客服或服務保證**，可能因故調整或中止服務
- 使用前工具會請你先詳閱一份使用須知並同意，才能開始使用

This is a free, personally-maintained tool — not a commercial product. A few things worth knowing upfront:

- You'll need your own free [Groq API Key](https://console.groq.com/keys) (a short guide is built into the tool, no credit card required)
- Your voice **is uploaded to Groq's servers** for transcription; the raw audio is discarded afterward, only the transcribed text is kept
- If you use the meeting summary feature, your transcript **is uploaded to Google Gemini's servers** for summarization (requires your own optional Gemini API Key)
- If you use the "Shared Notes" feature, the Sheet link you paste is used to send a read request to **Google's document servers**
- Your Groq/Gemini Keys and saved cards/summaries live in **your own device's browser storage**; if you're on a shared device, please use the built-in "clear local data" option afterward
- **Not recommended** for sensitive content (business secrets, personal data of others, passwords, ID numbers, etc.)
- This is a personal side project with **no formal support guarantee** and may change or be discontinued
- You'll be asked to read and agree to a short usage notice before first use

---

## 技術架構 / Tech stack

純前端 LINE LIFF 應用，單一 HTML 檔案，無後端伺服器：

- **LIFF SDK**：好友身份驗證、登入、傳送訊息、分享目標選擇
- **MediaRecorder API**：瀏覽器端錄音
- **Groq Whisper API**（`whisper-large-v3-turbo`）：語音轉文字
- **Google Gemini API**：會議摘要生成（選填功能）
- **Google Sheets CSV 匯出端點**：讀取共享筆記表格，搭配自製的簡易 CSV parser（處理雙引號跳脫、逗號、換行）
- **opencc-js**：簡體轉繁體轉換
- **localStorage**：API Key、卡片草稿、會議摘要的本機持久化
- **Content-Security-Policy**：限制外部資源來源，並對關鍵 CDN 資源加上 SRI 完整性驗證

A pure front-end LINE LIFF app, single HTML file, no backend server:

- **LIFF SDK** for friendship verification, login, message sending, and share target picker
- **MediaRecorder API** for in-browser audio recording
- **Groq Whisper API** (`whisper-large-v3-turbo`) for transcription
- **Google Gemini API** for meeting summary generation (optional)
- **Google Sheets CSV export endpoint** for reading shared notes, paired with a hand-written CSV parser (handles quoted-field escaping, commas, and line breaks)
- **opencc-js** for Simplified-to-Traditional Chinese conversion
- **localStorage** for persisting API keys, card drafts, and meeting summaries locally
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

個人專案，暫無正式授權條款。如有合作或使用上的疑問，歡迎透過 Issues 或官方帳號聯繫。

Personal project, no formal license specified yet. Feel free to reach out via Issues or the official LINE account for questions.
