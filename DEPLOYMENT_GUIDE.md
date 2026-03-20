# 🎮 GamePlanet 遊戲星球 — 完整部署指南

## 📁 檔案清單

| 檔案 | 用途 |
|------|------|
| `index.html` | 主程式（單一檔案，包含全部 200 款遊戲） |
| `DEPLOYMENT_GUIDE.md` | 本文件 — 部署指南 |
| `AD_GUIDE.md` | 廣告嵌入指南（附程式碼範例） |

---

## 🚀 部署到 GitHub Pages

### 步驟 1：建立 Repository
1. 到 https://github.com → 點擊 **New repository**
2. 名稱輸入 `gameplanet`（或任意名稱）
3. 選擇 **Public**
4. 點擊 **Create repository**

### 步驟 2：上傳檔案
1. 點擊 **uploading an existing file**
2. 拖曳 `index.html` 上傳
3. 點擊 **Commit changes**

### 步驟 3：啟用 GitHub Pages
1. 進入 **Settings** → **Pages**
2. Source 選擇 **Deploy from a branch**
3. Branch 選擇 **main** / **(root)**
4. 點擊 **Save**
5. 約 1-2 分鐘後，網站會在 `https://你的帳號.github.io/gameplanet/` 上線

---

## 🤖 Antigravity.ai 嵌入指南

### 什麼是 Antigravity.ai
Antigravity.ai 是一個 AI 驅動的聊天助手，可以嵌入到你的網站中，為玩家提供遊戲推薦和攻略建議。

### 嵌入步驟

#### 步驟 1：註冊帳號
1. 前往 https://antigravity.ai
2. 點擊 **Sign Up** 建立帳號
3. 建立一個新的 **Project**

#### 步驟 2：取得嵌入代碼
1. 在 Antigravity.ai 後台進入你的 Project
2. 點擊 **Embed** 或 **Integration**
3. 複製提供的 iframe 嵌入代碼，格式類似：

```html
<iframe 
  src="https://app.antigravity.ai/embed/你的PROJECT_ID" 
  width="100%" 
  height="400" 
  frameborder="0"
  allow="microphone"
  style="border-radius:12px;">
</iframe>
```

#### 步驟 3：嵌入到 GamePlanet
在 `index.html` 中搜尋以下區塊：

```html
<div class="antigravity-embed" id="antigravityEmbed">
  <div style="text-align:center;padding:24px">
    <div style="font-size:28px;margin-bottom:8px">🤖</div>
    <div style="color:#a78bfa;font-weight:600;margin-bottom:4px">Antigravity.ai 嵌入區域</div>
    <div style="font-size:11px">在此處放置您的 Antigravity.ai iframe 嵌入代碼</div>
  </div>
</div>
```

**替換成：**

```html
<div class="antigravity-embed" id="antigravityEmbed">
  <iframe 
    src="https://app.antigravity.ai/embed/你的PROJECT_ID" 
    width="100%" 
    height="400" 
    frameborder="0"
    allow="microphone"
    style="border-radius:12px;border:none;">
  </iframe>
</div>
```

#### 步驟 4：自訂 AI 助手
在 Antigravity.ai 後台可以設定：
- **System Prompt**：`你是遊戲星球的 AI 助手，幫助玩家推薦遊戲、提供攻略建議。網站有 200 款免費瀏覽器遊戲，包含懷舊經典、動作、益智、射擊、運動、策略等分類。`
- **歡迎訊息**：`🎮 歡迎來到遊戲星球！我可以幫你推薦遊戲或提供攻略，想玩什麼類型的遊戲呢？`
- **主題色**：設為 `#6366f1`（紫色）與網站風格搭配

---

## 📊 網站架構

```
index.html
├── <head>
│   ├── Google Fonts（Orbitron + Noto Sans TC + Press Start 2P）
│   └── <style>（全部 CSS，含 RWD）
├── <body>
│   ├── .bg-stars（背景星空粒子動畫）
│   ├── .page-wrapper（三欄式 Grid Layout）
│   │   ├── header（Logo + 搜尋框 + Antigravity 按鈕）
│   │   ├── nav（9 個分類標籤）
│   │   ├── ad-sidebar.left（左側廣告 160×600）
│   │   ├── main
│   │   │   ├── .hero-banner（主視覺橫幅）
│   │   │   ├── .antigravity-section（AI 助手嵌入區）
│   │   │   ├── .ad-banner-inline（橫幅廣告 728×90）
│   │   │   ├── #hotGames（熱門推薦）
│   │   │   ├── #retroGames（懷舊經典）
│   │   │   ├── .ad-banner-inline（橫幅廣告 728×90）
│   │   │   ├── #newGames（最新上架）
│   │   │   ├── #categoryCloud（分類標籤雲）
│   │   │   └── #allGames（全部遊戲）
│   │   ├── ad-sidebar.right（右側廣告 160×600 + 160×250）
│   │   └── footer
│   ├── #scrollTop（回到頂部按鈕）
│   ├── #bgmBtn（BGM 音樂開關）
│   └── #gameModal（遊戲彈窗）
│       ├── .game-modal-header（遊戲名稱 + 返回按鈕）
│       └── .game-modal-body
│           ├── .game-frame-container（遊戲區）
│           └── .game-modal-ad（遊戲內側邊廣告）
└── <script>
    ├── BGM（大廳背景音樂）
    ├── SFX（遊戲音效引擎）
    ├── GAMES[]（200 款遊戲資料）
    ├── CATS{}（9 大分類）
    ├── Render（渲染卡片/分類/搜尋）
    ├── openGame / closeGame / restartGame / _startGame
    ├── gameOver()（統一遊戲結束覆蓋層）
    └── GM{}（200 款遊戲實作）
```
