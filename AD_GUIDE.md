# 📢 GamePlanet 廣告嵌入完整指南

本文件說明 GamePlanet 網站中所有廣告版位的位置、尺寸、以及如何嵌入廣告代碼。

---

## 📍 廣告版位總覽（共 7 個版位）

| 編號 | 版位名稱 | 尺寸 | 位置 | 可見性 |
|------|----------|------|------|--------|
| A1 | 左側邊欄 | 160×600 | 主頁面左側 | 桌面版 |
| A2 | 右側邊欄上 | 160×600 | 主頁面右側上方 | 桌面版 |
| A3 | 右側邊欄下 | 160×250 | 主頁面右側下方 | 桌面版 |
| A4 | 橫幅廣告上 | 728×90 | 熱門推薦上方 | 全裝置 |
| A5 | 橫幅廣告下 | 728×90 | 懷舊經典下方 | 全裝置 |
| A6 | 遊戲內側邊上 | 160×300 | 遊戲彈窗右側 | 桌面版 |
| A7 | 遊戲內側邊下 | 160×250 | 遊戲彈窗右側 | 桌面版 |

> ⚠️ 側邊欄廣告（A1-A3、A6-A7）在手機版（<900px）自動隱藏

---

## 🔧 嵌入方式

### 使用 Google AdSense

1. 在 https://adsense.google.com 建立帳號並取得核准
2. 建立廣告單元，取得代碼

### 使用其他廣告聯盟

一般廣告聯盟會提供 `<script>` 或 `<iframe>` 代碼，按以下方式嵌入即可。

---

## 📋 各版位嵌入教學

### 🔹 A1：左側邊欄（160×600）

**在 HTML 中搜尋：**
```html
<!-- LEFT AD -->
<aside class="ad-sidebar left">
  <div class="ad-slot"><div class="ad-label">廣告空間</div><div>160×600</div></div>
</aside>
```

**替換成：**
```html
<!-- LEFT AD -->
<aside class="ad-sidebar left">
  <div class="ad-slot">
    <!-- 在這裡貼上你的 160x600 廣告代碼 -->
    <ins class="adsbygoogle"
         style="display:inline-block;width:160px;height:600px"
         data-ad-client="ca-pub-你的ID"
         data-ad-slot="你的廣告單元ID"></ins>
    <script>(adsbygoogle = window.adsbygoogle || []).push({});</script>
  </div>
</aside>
```

---

### 🔹 A2 + A3：右側邊欄（160×600 + 160×250）

**在 HTML 中搜尋：**
```html
<!-- RIGHT AD -->
<aside class="ad-sidebar right">
  <div class="ad-slot"><div class="ad-label">廣告空間</div><div>160×600</div></div>
  <div class="ad-slot" style="min-height:250px"><div class="ad-label">廣告空間</div><div>160×250</div></div>
</aside>
```

**替換成：**
```html
<!-- RIGHT AD -->
<aside class="ad-sidebar right">
  <div class="ad-slot">
    <!-- A2: 160x600 廣告 -->
    <ins class="adsbygoogle"
         style="display:inline-block;width:160px;height:600px"
         data-ad-client="ca-pub-你的ID"
         data-ad-slot="A2廣告單元ID"></ins>
    <script>(adsbygoogle = window.adsbygoogle || []).push({});</script>
  </div>
  <div class="ad-slot">
    <!-- A3: 160x250 廣告 -->
    <ins class="adsbygoogle"
         style="display:inline-block;width:160px;height:250px"
         data-ad-client="ca-pub-你的ID"
         data-ad-slot="A3廣告單元ID"></ins>
    <script>(adsbygoogle = window.adsbygoogle || []).push({});</script>
  </div>
</aside>
```

---

### 🔹 A4：橫幅廣告上（728×90）— 在熱門推薦上方

**在 HTML 中搜尋（第一個出現的）：**
```html
<div class="ad-banner-inline"><div class="ad-label" ...>廣告空間</div>728×90 Leaderboard</div>
```

**替換成：**
```html
<div class="ad-banner-inline">
  <!-- A4: 728x90 橫幅廣告 -->
  <ins class="adsbygoogle"
       style="display:inline-block;width:728px;height:90px"
       data-ad-client="ca-pub-你的ID"
       data-ad-slot="A4廣告單元ID"></ins>
  <script>(adsbygoogle = window.adsbygoogle || []).push({});</script>
</div>
```

---

### 🔹 A5：橫幅廣告下（728×90）— 在懷舊經典下方

與 A4 相同方式，替換第二個 `ad-banner-inline` 區塊。

---

### 🔹 A6 + A7：遊戲內側邊廣告（160×300 + 160×250）

**在 HTML 中搜尋：**
```html
<div class="game-modal-ad">
  <div class="ad-slot"><div class="ad-label">廣告空間</div><div>160×300</div></div>
  <div class="ad-slot" style="min-height:250px"><div class="ad-label">廣告空間</div><div>160×250</div></div>
</div>
```

**替換成：**
```html
<div class="game-modal-ad">
  <div class="ad-slot">
    <!-- A6: 遊戲內 160x300 -->
    <ins class="adsbygoogle"
         style="display:inline-block;width:160px;height:300px"
         data-ad-client="ca-pub-你的ID"
         data-ad-slot="A6廣告單元ID"></ins>
    <script>(adsbygoogle = window.adsbygoogle || []).push({});</script>
  </div>
  <div class="ad-slot">
    <!-- A7: 遊戲內 160x250 -->
    <ins class="adsbygoogle"
         style="display:inline-block;width:160px;height:250px"
         data-ad-client="ca-pub-你的ID"
         data-ad-slot="A7廣告單元ID"></ins>
    <script>(adsbygoogle = window.adsbygoogle || []).push({});</script>
  </div>
</div>
```

---

### 🔹 AdSense 全域腳本

在 `<head>` 區塊加入 AdSense 全域腳本（只需一次）：

```html
<script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-你的ID"
     crossorigin="anonymous"></script>
```

**搜尋：**
```html
<link href="https://fonts.googleapis.com/css2?family=...
```

**在該行上方加入：**
```html
<script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-你的ID" crossorigin="anonymous"></script>
```

---

## 💡 廣告最佳實踐

1. **不要放太多廣告** — Google 建議每頁不超過 3 個 AdSense 廣告單元
2. **遊戲內廣告注意體驗** — A6、A7 只在桌面版顯示，手機版自動隱藏
3. **橫幅廣告響應式** — A4、A5 可改用 AdSense 響應式廣告單元自動適配
4. **首次載入** — 廣告需要網站有真實流量才會顯示
5. **測試模式** — 開發期間在 AdSense 後台啟用測試模式

---

## 📊 廣告版位示意圖

```
┌──────────────────────────────────────────────┐
│                   HEADER                      │
├──────────────────────────────────────────────┤
│                    NAV                        │
├────────┬──────────────────────┬──────────────┤
│        │    ┌─── A4 (728×90)─┐│              │
│  A1    │    │  熱門推薦       ││    A2       │
│160×600 │    │  懷舊經典       ││  160×600    │
│        │    ├─── A5 (728×90)─┤│              │
│        │    │  最新上架       ││    A3       │
│        │    │  分類標籤       ││  160×250    │
│        │    │  全部遊戲       ││              │
├────────┴──────────────────────┴──────────────┤
│                   FOOTER                      │
└──────────────────────────────────────────────┘

遊戲彈窗：
┌──────────────────────────────────────────────┐
│  🎮 遊戲名稱                        ✕ 返回  │
├─────────────────────────────┬────────────────┤
│                             │    A6          │
│       遊戲畫面               │  160×300       │
│                             │                │
│                             │    A7          │
│                             │  160×250       │
└─────────────────────────────┴────────────────┘
```
