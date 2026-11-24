# 心靈微光・夢想國度

> SEASONS OF LIFE / SEL：一個以 3D 自然世界陪伴的社會情緒學習（SEL）與生命教育探索空間。

學生可以在海邊、森林、雪山、星空等 60 多個自然場景中漫遊，和動物夥伴互動，搭配呼吸練習、正念引導、情緒日記、感恩花園等活動，用自己的步調覺察和整理情緒。整個網站是一個 HTML 檔，不需要安裝任何套件。

---

## ✨ 功能

| 類別 | 內容 |
| --- | --- |
| 🌊 自然世界 | 60 多個 3D 場景（預設為**海邊**），可切換季節、時間、天氣、溫度和氛圍；支援第一人稱漫遊和自動運鏡 |
| 🐾 動物夥伴 | 點選動物後可以餵食、撫摸、聽叫聲、命名，也能換配件、毛色和動作 |
| 🏡 空間建造 | 心靈花園場景編輯、地形雕刻、木屋室內布置、種植與澆水 |
| 🧘 心靈練習 | 呼吸同步、正念引導、五感覺察、ASMR 自然音混音 |
| 📓 SEL 反思 | SEL 五大核心能力、生命故事思辨、情緒星圖、心情日曆、時光膠囊 |
| 🎨 創作 | 音樂工作室、自由繪畫畫布、明信片、故事書、作品集匯出 |
| 👩‍🏫 教學 | 教師教學模式、學習反思單下載 |

所有功能面板**預設收合**。可以用右側的「功能搜尋」、快速導覽或分類標籤找到需要的功能。

---

## 📁 專案結構

```
sel-world/
├── index.html              # 首頁（整個應用程式，含 CSS 與 JavaScript）
├── manifest.webmanifest    # PWA 設定（名稱、圖示、主題色、顯示模式）
├── sw.js                   # Service Worker（離線快取）
├── icons/
│   ├── favicon-32.png          # 瀏覽器分頁圖示
│   ├── apple-touch-icon.png    # iOS 主畫面圖示 180×180
│   ├── icon-192.png            # PWA 圖示 192×192
│   ├── icon-512.png            # PWA 圖示 512×512
│   └── icon-maskable-512.png   # Android 自適應圖示
├── .nojekyll               # 讓 GitHub Pages 直接提供靜態檔
├── .gitignore
└── README.md
```

---

## 🚀 上傳到 GitHub 並用 GitHub Pages 發布

### 方法 A：網頁操作（不需要指令）

1. 登入 GitHub，按右上角 **＋ → New repository**，例如命名為 `sel-world`，選 **Public**，再按 **Create repository**。
2. 在新的儲存庫頁面點 **uploading an existing file**，把本資料夾的**所有檔案和 `icons` 資料夾**拖進去，再按 **Commit changes**。
   - `.nojekyll`、`.gitignore` 是隱藏檔，若拖曳時沒帶上，可以用 **Add file → Create new file** 自行建立（`.nojekyll` 內容留空即可）。
3. 進入 **Settings → Pages**，**Source** 選 **Deploy from a branch**，Branch 選 `main`、資料夾選 `/ (root)`，按 **Save**。
4. 等待約 1–2 分鐘，網址會是：`https://<你的帳號>.github.io/sel-world/`

### 方法 B：Git 指令

```bash
cd sel-world
git init
git add .
git commit -m "首次發布：心靈微光・夢想國度"
git branch -M main
git remote add origin https://github.com/<你的帳號>/sel-world.git
git push -u origin main
```

推送後，再依照方法 A 的第 3 步開啟 GitHub Pages。

> ⚠️ 請勿上傳任何 API 金鑰或私密設定檔（例如語音服務金鑰 `.txt`）。`.gitignore` 已預先排除常見的金鑰檔名。

---

## 📱 PWA（安裝成 App）

網站符合 PWA 條件，透過 **HTTPS** 開啟後（GitHub Pages 預設就是 HTTPS）可以安裝：

- **電腦 Chrome / Edge**：網址列右側會出現安裝圖示，也可以按頁首的「**安裝 App**」按鈕。
- **Android Chrome**：選單 → **加到主畫面／安裝應用程式**。
- **iPhone / iPad Safari**：分享按鈕 → **加入主畫面**。

**離線使用**：第一次連線開啟後，Service Worker 會快取網頁、圖示、Three.js 和字型，之後沒有網路也能開啟。

**發布新版本**：修改 `index.html` 後，請把 `sw.js` 最上方的 `CACHE_VERSION` 改成下一個版本（例如 `'v2'`），使用者重新開啟兩次就會看到新版。

---

## 📐 RWD 響應式設計

| 螢幕 | 版面 |
| --- | --- |
| 大螢幕（≥1600px） | 3D 場景加寬版功能面板，字級放大 |
| 桌機／筆電 | 左側 3D 場景、右側功能面板，兩欄並排 |
| 平板（801–1100px） | 兩欄，面板縮窄 |
| 手機直向（≤800px） | 單欄；3D 場景固定在上方，功能面板在下方捲動 |
| 小手機（≤480px） | 頁首按鈕平均分配，浮動資訊縮小 |
| 手機橫向 | 恢復左右兩欄，場景填滿螢幕高度 |
| 觸控裝置 | 按鈕和勾選框至少 44px，方便手指點按 |

也支援 iPhone 瀏海與圓角的安全區域（safe-area）。

---

## 🔒 隱私說明

- 日記、感恩花園、情緒星圖、時光膠囊等內容**只存在使用者自己的瀏覽器（localStorage）**，不會上傳到任何伺服器。
- 在共用電腦上請勿保存私密內容，用完可以按各功能的「清除」按鈕刪除。
- 環境音和動物叫聲都由程式合成，不是真實錄音；溫度、氣味、觸感等為想像引導。

---

## 🛠 技術

- [Three.js](https://threejs.org/) 0.170.0（由 jsDelivr CDN 載入）
- 原生 HTML / CSS / JavaScript，不需要建置工具
- Google Fonts：Noto Sans TC、Noto Serif TC
- Web Audio API、Canvas、localStorage、Service Worker、Web App Manifest

## 💻 在本機預覽

Service Worker 需要透過 `http://localhost` 或 HTTPS 執行，直接雙擊 HTML 檔時 PWA 功能不會啟用。可以在資料夾中執行：

```bash
python -m http.server 8000
```

再開啟 <http://localhost:8000>。

## 🌐 瀏覽器支援

建議使用最新版的 Chrome、Edge、Safari 或 Firefox。需要支援 WebGL。
