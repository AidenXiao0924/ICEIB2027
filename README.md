# DIC4 — ICEIB 2027 / DietSense

物聯網應用與資料分析作業：IEEE Conference 論文初稿、MCP 輔助開發與 GitHub 上的 OpenSpec。

## 專案結構

- [ICEIB2027-IEEE/](ICEIB2027-IEEE/)：IEEEtran 論文、六個章節、BibTeX、TikZ 圖及表格。
- [openspec/](openspec/)：研究需求、設計、提案與待辦；目前是 proposed change，非已完成的系統規格。
- [docs/mcp-setup.md](docs/mcp-setup.md)：Antigravity Git MCP 與 Overleaf Web MCP 安裝、設定及驗證方法。
- [docs/workflow.md](docs/workflow.md)：論文、GitHub、Overleaf 與 OpenSpec 工作流程。
- `.mcp.json`、`.vscode/mcp.json`：其他相容客戶端的 Git MCP 與 Overleaf Web MCP 設定範例，未包含登入憑證；請按本機路徑調整。

## 研究內容

DietSense 結合 ESP32/MQTT 室內溫濕度、SQLite 資料、Python 分析、CWA 鄉鎮天氣預報及住戶確認，設計可追溯證據的對話式建議 Agent。兩週單室試驗及固定規則／淺層決策樹比較仍屬規劃，未宣稱已完成實驗。

## DIC4 工作紀錄

1. Windows 已確認 Git 2.56.0.windows.2、uv/uvx 0.13.10 可用。
2. Overleaf Git Integration 顯示 Premium 限制，因此下載原始碼 ZIP，於本機建立 Git repository，初始 commit 為 `06830f3`。
3. Antigravity 全域 MCP 設定使用 `uvx mcp-server-git --repository <local-repository>`，伺服器名稱 `paper-DIC4`。
4. 初次 Agent 檢查未辨識延遲載入的 MCP 工具；使用內建 antigravity-guide 後，Agent 回報成功呼叫 `paper-DIC4/git_status` 與 `paper-DIC4/git_log`，確認當時分支 master、工作區乾淨及初始 commit。模型 HTTP 503 是當時的容量錯誤，不是 MCP 驗證失敗。
5. GitHub main 已包含原始論文。Commit `317af40` 將單檔論文拆成實際章節、圖表及 BibTeX，並加入 OpenSpec 提案。
6. 本次整理將論文集中於 ICEIB2027-IEEE/，補充可重現 MCP 設定與工作紀錄，保留 Git 歷史及 OpenSpec。

## 編譯與同步

將 ICEIB2027-IEEE/ **內的內容**上傳 Overleaf，選 main.tex、pdfLaTeX，執行 BibTeX 並重新編譯。亦可在該目錄執行 `latexmk -pdf main.tex`。目前已加入第三方 Overleaf Web MCP 1.3.0 設定；需在使用端完成 Node.js 安裝、Overleaf 登入及連線測試後，才能透過 MCP 讀取專案、同步及遠端編譯。尚未實測，手動同步仍可使用。

## OpenSpec

參見 [研究提案](openspec/changes/define-evidence-grounded-agent/proposal.md)、[設計](openspec/changes/define-evidence-grounded-agent/design.md)、[需求](openspec/changes/define-evidence-grounded-agent/specs/evidence-grounded-advice/spec.md) 與 [任務](openspec/changes/define-evidence-grounded-agent/tasks.md)。安裝官方 CLI 後在 repository 根目錄執行 `openspec validate define-evidence-grounded-agent --strict`。尚未執行 CLI 驗證。

本次參考組員的目錄分層與工作紀錄方式，未複製其研究原稿或登入設定。架構圖以 TikZ 原始碼保留，不另附尚未產生的 architecture.pdf。
