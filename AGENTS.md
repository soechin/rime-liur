# Rime 嘸蝦米 (liur) 設定方案

## 專案概觀
本專案包含 **Rime (中州韻輸入法引擎)** 上的 **嘸蝦米輸入法 (liur)** 設定檔。此方案旨在提供完整的嘸蝦米輸入體驗，支援繁體中文、擴充字集，並具備多種反查功能。

## 目錄結構

```
rime-liur/
├── Rime/                          # Rime 方案主目錄
│   ├── liur.schema.yaml           # 主方案定義檔
│   ├── liur.extended.dict.yaml    # 詞庫進入點
│   ├── liur.custom.yaml           # 方案自訂設定
│   ├── liur_Trad.dict.yaml        # 常用繁體詞庫
│   ├── liur_TradExt.dict.yaml     # 繁體擴充詞庫
│   ├── liur_TradToSimp.dict.yaml  # 繁簡對照詞庫
│   ├── liur_Japan.dict.yaml       # 日文漢字詞庫 (選用)
│   ├── liur_customWords.dict.yaml # 使用者自定義詞彙
│   ├── default.custom.yaml        # Rime 全域自訂設定
│   ├── squirrel.custom.yaml       # macOS 鼠鬚管介面設定
│   ├── weasel.custom.yaml         # Windows 小狼毫介面設定
│   └── opencc/                    # OpenCC 字碼轉換
│       ├── liu_w2c.json           # 字碼反查設定檔
│       ├── liu_w2c.txt            # 常用字字碼對照表
│       ├── liu_w2cExt.txt         # 擴充字字碼對照表
│       └── liu_w2cJp.txt          # 日文漢字字碼對照表
├── Deploy.bat                     # Windows 部署腳本
├── Install.bat                    # Windows 安裝腳本
└── rime_liur_installer.sh         # macOS/Linux 安裝腳本
```

## 關鍵檔案說明

### 方案定義
-   **`liur.schema.yaml`**: 核心方案定義檔。定義了：
    +   **引擎處理器 (Processors):** 包含按鍵綁定、組詞與翻譯邏輯。
    +   **切換開關 (Switches):** 包含中英文切換、全半角、簡繁轉換及字碼反查。
    +   **翻譯器 (Translators):**
        *   `translator`: 主打嘸蝦米輸入（查表式）。
        *   `mkst`: 造詞功能（引導鍵：`;`）。
        *   `liurqry`: 讀音反查（引導鍵：`;;`）。
        *   `phonetic`: 注音反查（引導鍵：`';`）。

### 詞庫檔案
-   **`liur.extended.dict.yaml`**: 詞庫主進入點。匯入其他字典檔並定義自動組詞規則。
    +   **組詞公式:**
        *   2 字詞：`AaBaBaBa`（字1首碼 + 字2首碼 x3）
        *   3 字詞：`AaBaCaCa`（字1首碼 + 字2首碼 + 字3首碼 x2）
        *   4~10 字詞：`AaBaCaZa`（字1首碼 + 字2首碼 + 字3首碼 + 末字首碼）
    +   **匯入項目:** `liur_Trad`、`liur_TradExt`、`liur_customWords`
-   **`liur_Trad.dict.yaml`**: 常用繁體字詞庫。
-   **`liur_TradExt.dict.yaml`**: 繁體擴充字集詞庫（含罕用字）。
-   **`liur_TradToSimp.dict.yaml`**: 繁簡對照詞庫。
-   **`liur_Japan.dict.yaml`**: 日文漢字詞庫（預設停用，需在 `liur.extended.dict.yaml` 取消註解啟用）。
-   **`liur_customWords.dict.yaml`**: 使用者自定義詞彙。

### OpenCC 字碼轉換
-   **`opencc/` 目錄**: 用於字碼反查功能。
    +   **`liu_w2c.json`**: 反查功能設定，整合以下對照表：
    +   **`liu_w2c.txt`**: 常用字的嘸蝦米拆碼對照表。
    +   **`liu_w2cExt.txt`**: 擴充字集的嘸蝦米拆碼對照表。
    +   **`liu_w2cJp.txt`**: 日文漢字的嘸蝦米拆碼對照表。

### 客製化設定
-   **`default.custom.yaml`**: Rime 全域自定義設定（選單、按鍵綁定等）。
-   **`liur.custom.yaml`**: 針對此方案的特定設定（建議在此處修改以避免更動原始 schema）。
-   **`squirrel.custom.yaml`**: macOS 鼠鬚管介面設定（外觀、配色等）。
-   **`weasel.custom.yaml`**: Windows 小狼毫介面設定。

## 使用與安裝

1.  **部署**:
    -   將 `Rime/` 目錄下的所有檔案複製到 Rime 的使用者資料夾：
        +   **macOS (Squirrel):** `~/Library/Rime/`
        +   **Windows (Weasel):** `%APPDATA%\Rime`
    -   或使用安裝腳本：
        +   **macOS/Linux:** `./rime_liur_installer.sh`
        +   **Windows:** 執行 `Install.bat`
    -   執行 Rime 的 **「重新部署」 (Deploy)** 功能。

2.  **輸入功能**:
    -   **一般輸入**: 直接輸入嘸蝦米字碼。
    -   **注音反查**: 以 `';` 開頭。
    -   **讀音反查**: 以 `;;` 開頭。
    -   **自定義造詞**: 以 `;` 開頭。

## 開發與貢獻
-   **修改詞庫**: 可直接在 `Rime/liur_customWords.dict.yaml` 新增詞彙。
-   **調整功能**: 建議透過 `Rime/liur.custom.yaml` 進行覆蓋設定，以維持原始設定檔的整潔。
-   **啟用日文漢字**: 編輯 `Rime/liur.extended.dict.yaml`，取消 `liur_Japan` 的註解。
