# MCP 設定與驗證

本專案已實測的是 Git MCP，而非 Overleaf 遠端 MCP。先安裝 Git 和 uv，確認 git --version 與 uvx --version 正常。

## Antigravity（Windows）

全域設定檔：`%USERPROFILE%\.gemini\config\mcp_config.json`。合併既有設定，不覆蓋其他 servers。以實際 Git 根目錄取代範例路徑（JSON 反斜線需跳脫）。

```json
{
  "mcpServers": {
    "paper-DIC4": {
      "command": "uvx",
      "args": ["mcp-server-git", "--repository", "C:/path/to/ICEIB2027"]
    }
  }
}
```

重新開啟對話或 IDE，請 Agent 呼叫 git_status、git_log，repo_path 指向 Git 根目錄。若未直接顯示工具，使用 antigravity-guide 檢查 lazy-loaded tools 與 call_mcp_tool。可用 `uvx mcp-server-git --help` 診斷套件啟動。

實際測試紀錄（使用者提供的 Agent 日誌）：
- Used MCP tool: paper-DIC4/git_status
- Used MCP tool: paper-DIC4/git_log
- 當時分支 master，working tree clean，commit 06830f37f934cace0dead365c1f47cd53c3e564c。
- Agent 回報探索到 14 個工具。此紀錄屬初始本機版本，不代表本次 GitHub 重構已在本機測試。

## 其他客戶端

根目錄 .mcp.json 使用相對路徑 "."，需從 repository 根目錄啟動支援的客戶端，若 cwd 不同請改成絕對路徑。VS Code 範例使用 workspaceFolder，請開啟 Git 根目錄。兩份範例尚未實機驗證，不是 Antigravity 全域設定的替代品。

## GitHub / Overleaf

Git MCP 可檢查差異與建立本機 commit；push/pull 由 Git CLI 處理。GitHub 登入授權與 Overleaf Token 不同。禁止提交 Token 或 session。若憑證曾公開，應撤銷後重新產生。

## Overleaf Web MCP（新增設定，尚待本機驗證）

使用第三方 [overleaf-web-mcp](https://github.com/mhmdaskari/overleaf-web-mcp) 1.3.0；非 Overleaf 官方服務。依套件文件，核心工作流程使用網頁登入 session，不需要付費 Git Integration，但受帳號權限與服務限制。安裝前確認來源與使用條款。

### Windows 安裝

在 PowerShell 執行（已安裝 Node.js 20+ 可跳過安裝）：

```powershell
winget install --id OpenJS.NodeJS.LTS -e
```

重新開啟終端機後：

```powershell
node --version
npm.cmd --version
npx.cmd -y overleaf-web-mcp@1.3.0 login
npx.cmd -y overleaf-web-mcp@1.3.0 call auth_status
```

在專用瀏覽器視窗自行登入 Overleaf；不要把 Cookie、Token 或密碼寫入 GitHub。

### Antigravity 雙 MCP 設定

合併到既有全域設定檔（保留其他 servers，替換 Git 路徑）：

```json
{
  "mcpServers": {
    "paper-DIC4": {
      "command": "uvx",
      "args": ["mcp-server-git", "--repository", "C:/path/to/ICEIB2027"]
    },
    "overleaf": {
      "command": "npx.cmd",
      "args": ["-y", "overleaf-web-mcp@1.3.0", "serve"]
    }
  }
}
```

若找不到 npx.cmd，執行 `(Get-Command npx.cmd).Source`，將完整路徑填入 command。重新啟動 IDE。根目錄 .mcp.json 與 .vscode/mcp.json 亦已加入此 server；其他客戶端須依其啟動方式調整。不要直接信任或執行未審查的第三方設定。

### 操作與驗證

1. auth_status 確認登入，list_projects 列出專案，核對正確專案 ID。
2. get_project_tree 檢查雲端目錄，必要時 read_file 讀取內容。
3. plan_sync 指定本機 ICEIB2027-IEEE/ 的絕對路徑，檢查同步差異；共同作者的修改先備份及比對。
4. 經使用者確認後，依工具 schema 使用 sync_directory 與 planToken，採 additive 模式，避免刪除遠端檔案；tracked 寫入取決於帳號支援，不強制使用。
5. compile_project 編譯 main.tex，檢查 builtCleanly 與輸出；get_compile_log 查閱錯誤。
6. 修正後重新比對、同步與編譯。Git commit/push 仍走 Git 工作流程。

若登入過期，重新執行 login。以上是套件支援能力與待測流程，不是已取得的執行成果。參考 [安裝指南](https://mhmdaskari.github.io/overleaf-web-mcp/install/) 與 [工具文件](https://mhmdaskari.github.io/overleaf-web-mcp/tools/)。

