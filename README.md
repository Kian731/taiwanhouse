# 2031 台灣買房共識板

跨國、未婚伴侶在台灣購屋的互動式規劃頁，內容包含：

- 頭期款與個別儲蓄試算
- 青安與一般房貸判讀
- 貸款人、持分與共同購屋方案
- 2026–2031 行程、購屋流程及交屋後待辦
- 電梯大樓與未婚共同購屋檢查清單

這是一個無須安裝套件、無須建置的純靜態網站。

## 專案結構

```text
.
├─ .github/
│  └─ workflows/
│     └─ deploy-pages.yml   # GitHub Pages 自動部署
├─ dist/
│  ├─ .nojekyll             # 停用 Jekyll 處理
│  └─ index.html            # 網站本體
├─ .gitignore               # 排除本機與私有設定
├─ preview-server.mjs       # 本機預覽伺服器
└─ README.md
```

## 上傳並部署至 GitHub Pages

### 1. 建立 GitHub 儲存庫

在 GitHub 建立一個新的空白儲存庫，不需要另外建立 README、`.gitignore` 或 License。

> 注意：本網站包含薪資與財務假設。公開儲存庫與公開 GitHub Pages 任何人都能瀏覽，請先確認是否接受公開這些內容。

### 2. 推送目前專案

在此資料夾開啟 PowerShell，依序執行：

```powershell
git add .
git commit -m "Prepare site for GitHub Pages"
git remote add origin https://github.com/你的帳號/你的儲存庫.git
git push -u origin main
```

如果已經設定過 `origin`，請改用：

```powershell
git remote set-url origin https://github.com/你的帳號/你的儲存庫.git
git push -u origin main
```

### 3. 開啟 GitHub Pages

進入 GitHub 儲存庫：

1. 選擇 **Settings → Pages**。
2. 在 **Build and deployment** 的 **Source** 選擇 **GitHub Actions**。
3. 進入 **Actions** 查看 `Deploy website to GitHub Pages`。
4. 部署成功後，網址通常是 `https://你的帳號.github.io/你的儲存庫/`。

之後只要修改 `dist/` 內的網站檔案並推送到 `main`，GitHub Actions 就會自動重新部署。

## 本機預覽

需先安裝 Node.js。在此資料夾執行：

```powershell
node preview-server.mjs
```

然後開啟 <http://127.0.0.1:4173/>。結束預覽時按 `Ctrl+C`。

## 更新網站

主要內容都在 `dist/index.html`。修改並確認後執行：

```powershell
git add dist/index.html
git commit -m "Update home-buying plan"
git push
```

## 資料聲明

資料依 2026-10-12 可查得的官方資訊整理。政策、匯率、利率、稅制與各銀行授信標準可能變動，正式購屋前應重新向承辦銀行、地政士／律師及稅務機關確認。
