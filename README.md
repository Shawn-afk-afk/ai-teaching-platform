# AI 教學平台 Windows 測試版

此版本為本機測試版。使用者自行建立教師帳號及資料庫，請勿將 data、.venv、backups 或 ngrok 權杖上傳或分享。

1. 安裝 Node.js 24 以上、Python 3.12（含 Windows launcher）及 Ollama。安裝後重新開啟 PowerShell。
2. 解壓縮完整資料夾，在資料夾空白處開啟 PowerShell，執行 `powershell -ExecutionPolicy Bypass -File .\setup.ps1`。此步透過網路安裝 Python 依賴。
3. 啟動 Ollama，執行 `ollama pull gemma4:12b`；下載需網路、磁碟空間及可運行模型的硬體。

   本測試版固定核對模型 digest `6114515d63c17436a7c0417d82820ac65ad643e2806c5a3c89cb62846436ed0b`；若 Ollama 取得的模型版本不同，生成會顯示模型版本已變更，需要重新驗收，不能直接替換 digest 當作已驗證。
4. 執行 `powershell -ExecutionPolicy Bypass -File .\start-p7.ps1`，保持視窗開啟。到 http://127.0.0.1:4180/ ，首次依終端顯示的一次設定碼建立教師帳號（密碼至少 12 字元）。
5. 每位學生使用教師系統產生的獨立邀請碼。作品上傳、批改及教師審核政策見網站提示。AI 草稿需教師審核才發布。
6. 如要外網試用，從 ngrok 官方下載 ngrok.exe 至本資料夾，註冊帳號後執行 `New-Item -ItemType Directory -Force .\data\ngrok`，再執行 `.\ngrok.exe config add-authtoken '你的權杖' --config .\data\ngrok\ngrok.yml`。保存資料並停止舊網站後，雙擊 start-ngrok.bat。僅分享 PUBLIC URL 與各自學生邀請碼；不要分享權杖。
7. 備份：`powershell -ExecutionPolicy Bypass -File .\manage-p7.ps1 -Action backup -Destination '.\backups\backup-01'`，目的資料夾必須尚不存在。模型、原教材及生成續作資料需另行保存。

正式外網部署、資料保存政策及新硬體的效能尚須另行驗收。遊戲僅保留空位。
