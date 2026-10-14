### README（已更新）

# 2FA Dashboard 使用說明

## 檔案說明

- `VPN_2FA_Generator.pyw.template`：乾淨程式 Template（已清空所有 Secret / Prefix / Invitation Code）
- `config.json.template`：乾淨設定檔 Template
- 使用前請把兩個 Template 複製一份並改名：
  - `VPN_2FA_Generator.pyw.template` → `VPN_2FA_Generator.pyw`
  - `config.json.template` → `config.json`

## 安裝

在程式資料夾開啟終端機，執行：

```bash
pip install -r requirements.txt
```

`requirements.txt` 內容：

```txt
customtkinter
pyotp
pyperclip
pystray
pillow
```

## 第一次使用

1. 把 `VPN_2FA_Generator.pyw.template` 改名為 `VPN_2FA_Generator.pyw`
2. 把 `config.json.template` 改名為 `config.json`
3. 用下面「建立捷徑」的方式啟動程式
4. 因為尚未填入任何 Secret，程式會自動跳到 **Settings** 頁面
5. 在 Settings 填入各帳號的 Prefix 與 Secret
6. 按「儲存設定」後即可正常使用

> CyberArk 的 Prefix 是每次在 Generate 頁面上方輸入的，不需要在 Settings 填。

## 啟動方式（推薦）

使用桌面捷徑啟動，避免出現黑色 CMD 視窗。

### 建立捷徑

1. 在桌面空白處 → 右鍵 → **新增 → 捷徑**
2. 位置欄貼入：

```text
C:\Users\user\AppData\Local\Programs\Python\Python310\pythonw.exe "C:\Users\user\Documents\WorkPlace\VPN_2FA_Generator\VPN_2FA_Generator.pyw"
```

3. 按「下一步」→ 取個名字（例如：`2FA Dashboard`）→ 完成
4. 之後雙擊這個捷徑即可啟動

> 如果 `pythonw.exe` 路徑不正確，請在 CMD 輸入 `where pythonw` 查看正確路徑後再替換。

## 日常使用

1. 啟動後進入 **Generate** 頁面
2. 點擊對應帳號按鈕（T1 / P1 / P2 / CyberArk / Email），密碼會自動複製到剪貼簿
3. CyberArk 需要先在上方輸入今次 Prefix，再按按鈕
4. 下方可一鍵複製 EMS Invitation Code（需先在程式碼的 `INVITE_CODES` 填入內容才有效）

### 系統匣操作

- 按視窗右上角 **X** → 視窗隱藏，圖示出現在右下角系統匣
- 左鍵點系統匣圖示 → 重新顯示視窗
- 右鍵系統匣圖示 → 可選擇「顯示視窗」或「退出」

## 設定與檔案

- 所有設定會儲存在同資料夾的 `config.json`
- 程式已使用絕對路徑讀取設定檔，用捷徑啟動不會找不到檔案
- Invitation Code 目前寫在程式碼的 `INVITE_CODES` 字典裡，如需使用請自行填入
- 請勿將 Secret 或 `config.json` 貼到公開場合

## 注意事項

- 建議定期備份 `config.json`
- Secret 支援 Base32 或 Hex 格式
