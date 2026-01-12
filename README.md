# Rime 嘸蝦米輸入法方案

Rime 輸入法引擎上的嘸蝦米輸入法方案。

## 致謝

感謝其他人的貢獻。

## 功能熱鍵

| 功能 | 熱鍵 | 說明 |
|------|------|------|
| 方案選單 | ``Ctrl + Shift + ` `` | 喚起方案選單 |
| 注音反查 | `';` | 以注音查詢漢字 |
| 讀音反查 | `;;` | 輸入嘸蝦米碼反查該字讀音 |
| 自動造詞 | `;` | 動態造詞功能 |
| 字碼反查 | `Ctrl + '` | 查詢字的嘸蝦米編碼 |
| 簡繁轉換 | `Ctrl + .` | 即時切換簡繁體 |
| 擴充字集 | `Ctrl + /` | 切換至擴充字集（罕用字） |
| 中英切換 | `Shift` | 切換中英文輸入 |
| 中文上字 | `空白鍵` | 送出中文字或中文符號 |

## 安裝方式

### macOS（鼠鬚管）

1. 下載並安裝 [鼠鬚管](https://rime.im/download/)
2. Clone 本專案：
   ```bash
   git clone https://github.com/soechin/rime-liur.git
   ```
3. 執行安裝腳本或手動複製：
   - **腳本安裝：**
     ```bash
     cd rime-liur
     ./rime_liur_installer.sh
     ```
   - **手動複製：**
     1. 使用 plum 初始化注音輸入法：
        ```bash
        curl -fsSL https://git.io/rime-install | bash
        ```
     2. 將 `Rime/` 目錄下的檔案複製到 `~/Library/Rime/`
4. 點擊鼠鬚管選單，選擇「重新部署」

### Windows（小狼毫）

1. 下載並安裝 [小狼毫](https://rime.im/download/)
2. Clone 本專案：
   ```bash
   git clone https://github.com/soechin/rime-liur.git
   ```
3. 執行安裝腳本或手動複製：
   - **腳本安裝：** 執行 `Install.bat`
   - **手動複製：** 將 `Rime/` 目錄下的檔案複製到 `%APPDATA%\Rime`
4. 點擊小狼毫選單，選擇「重新部署」

## 自定義詞彙

編輯 `Rime/liur_customWords.dict.yaml`，格式如下：

```yaml
自定義文字<Tab>編碼
```

例如：`台北火車站	tptr`

修改後記得「重新部署」。
