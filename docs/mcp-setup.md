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

第三方 overleaf-web-mcp 是可另外評估的整合，不是本專案已安裝或已授權的工具；使用前應確認套件來源、權限、服務條款及帳號支援狀況。
