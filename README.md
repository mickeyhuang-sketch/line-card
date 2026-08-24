# line-card — Mickey 電子名片（LIFF）

LINE 個人帳號用的電子名片：點 LIFF 連結 → LINE 原生選好友畫面 → Flex Message 三卡名片以本人身分發出。

- 線上頁面：https://mickeyhuang-sketch.github.io/line-card/
- 名片卡片：`flex-message.json`（三張卡 carousel，可貼 [Flex Simulator](https://developers.line.biz/flex-simulator/) 驗證）
- 發送頁：`index.html`（LIFF init → shareTargetPicker → closeWindow）

## LINE Developers 設定步驟（一次性）

1. 開 https://developers.line.biz/console/ → 用你的 LINE 帳號登入
2. 建 Provider（已有就跳過，名稱隨意，例如 `mickey`）
3. **Create a new channel → LINE Login**
   - Channel name：`line-card`（對外不顯示）
   - Region：Taiwan
4. 進該 channel → **LIFF** 分頁 → **Add**
   - LIFF app name：`名片`
   - **Size：Full**
   - **Endpoint URL：`https://mickeyhuang-sketch.github.io/line-card/`**
   - Scopes：勾 `profile`
   - **Add friend option：Off（aggressive 不用開）**
5. 建好後同一頁把 **shareTargetPicker** 開關切到 **ON**（沒開會發不出去）
6. 複製 **LIFF ID**（形如 `1234567890-abcdefgh`），貼給可可 → 填進 `index.html` 的 `LIFF_ID` 後重新 push 即生效
7. Channel 保持 **Developing** 狀態即可（只有自己用，不用送審／Publish）

## 日常使用（存 Keep）

1. LIFF 連結格式：`https://liff.line.me/<LIFF_ID>`
2. LINE 裡打開「Keep 筆記」聊天室（主頁搜尋 Keep），把上面連結貼進去傳送一次
3. 之後要發名片：開 Keep → 點該連結 → 跳出選好友畫面 → 勾人 → 送出，名片就以你的身分發到對方聊天室
4. 也可以把連結釘選在 Keep 或加到任何自己的群組裡備用

## 檔案

| 檔案 | 用途 |
|---|---|
| `index.html` | LIFF 發送頁（含 Flex JSON 內嵌） |
| `flex-message.json` | 名片 Flex carousel（與 index.html 內嵌版同步，改文案兩邊一起改） |
| `person-side.png` | 卡 1 去背人像合成圖 |
| `logo.png` / `logo-white.png` | GoWarehouse 官方橫式 logo（藍字版／白字版） |
| `ibiza-logo.png` | IBIZA 公司 logo |
| `icon-*.png` | 按鈕與社群 icon（mail / li / fb / ig / yt / map） |

## 修改文案

改 `flex-message.json` 後，同步更新 `index.html` 內嵌的同一份 JSON（`const FLEX_CAROUSEL`），push 到 `main` 即自動部署（GitHub Pages，約 1 分鐘生效）。
