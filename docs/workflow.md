# DIC4 工作流程

1. 從 GitHub clone repository；既有本機先執行 git status、git remote -v，確認無衝突及 origin 正確，再 git pull --ff-only origin main。
2. 在 Git 根目錄開啟 IDE，使用 Git MCP 查看狀態及歷史。論文在 ICEIB2027-IEEE/。
3. 依照 OpenSpec proposed change 檢查研究需求、設計與待辦；未實作或未量測的事項保持未完成。
4. 若已安裝官方 OpenSpec CLI，從根目錄執行 openspec validate define-evidence-grounded-agent --strict；記錄實際結果。
5. 修改 LaTeX 後檢查 Git diff、引用、圖表及作者資訊。從論文子目錄以 latexmk -pdf main.tex 編譯，或將該目錄內容手動上傳 Overleaf 並編譯。
6. 確認內容與 PDF 後 commit、push，不使用 force push。共同作者的雲端修改應先比對，勿直接覆蓋。
7. 繳交最新 PDF、GitHub 連結；必要時附 MCP 呼叫證明及 Overleaf 唯讀連結。

## 目前限制

本次 GitHub 直接更新不會自動同步本機或 Overleaf。尚未執行 OpenSpec CLI 或最新 LaTeX 編譯。正式標題及作者待組員確認。兩週 pilot 尚未完成，不可填入假數據。
