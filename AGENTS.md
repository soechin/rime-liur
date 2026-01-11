# Rime 嘸蝦米 (liur) 設定方案

## 專案概觀
本專案包含 **Rime (中州韻輸入法引擎)** 上的 **嘸蝦米輸入法 (liur)** 設定檔。此方案旨在提供完整的嘸蝦米輸入體驗，支援繁體中文、擴充字集，並具備多種反查功能。

## 關鍵檔案與結構

### 方案定義
-   **`liur.schema.yaml`**: 核心方案定義檔。定義了：
    +   **引擎處理器 (Processors):** 包含按鍵綁定、組詞與翻譯邏輯。
    +   **切換開關 (Switches):** 包含中英文切換、全半角、簡繁轉換及字碼反查。
    +   **翻譯器 (Translators):**
        *   `translator`: 主打嘸蝦米輸入（查表式）。
        *   `mkst`: 造詞功能（引導鍵：`;`）。
        *   `liurqry`: 讀音反查（引導鍵：`;;`）。
        *   `pinyin`: 漢語拼音輸入（引導鍵：`` ` ``）。
        *   `phonetic`: 注音反查（引導鍵：`';`）。

### 詞庫檔案
-   **`liur.extended.dict.yaml`**: 詞庫主進入點。匯入其他字典檔並定義自動組詞規則（如：兩碼詞為字1首碼+字2首碼）。
    +   **匯入項目:** `liur_Trad` (常用繁體)、`liur_TradExt` (繁體擴充)、`liur_customWords` (自定義詞庫)。
-   **`liur_customWords.dict.yaml`**: 使用者自定義詞彙。
-   **`liur_English.dict.yaml`**: (選用) 英文詞庫。
-   **`liur_Japan.dict.yaml`**: (選用) 日文漢字詞庫。

### OpenCC 字碼轉換
-   **`opencc/` 目錄**: 用於字元轉換的設定。
    +   **`liu_w2c.json`**: 「字碼反查」設定，用於在輸入時顯示該字的嘸蝦米拆碼。

### 客製化設定
-   **`default.custom.yaml`**: Rime 全域自定義設定。
-   **`liur.custom.yaml`**: 針對此方案的特定設定（建議在此處修改以避免更動原始 schema）。
-   **`squirrel.custom.yaml` / `weasel.custom.yaml`**: 分別針對 macOS (鼠鬚管) 與 Windows (小狼毫) 的介面設定。

## 使用與安裝

1.  **部署**:
    -   將此目錄下的所有檔案複製到 Rime 的使用者資料夾：
        +   **macOS (Squirrel):** `~/Library/Rime/`
        +   **Windows (Weasel):** `%APPDATA%\Rime`
    -   執行 Rime 的 **「重新部署」 (Deploy)** 功能。

2.  **輸入功能**:
    -   **一般輸入**: 直接輸入嘸蝦米字碼。
    -   **拼音反查**: 以 `` ` `` 開頭。
    -   **注音反查**: 以 `';` 開頭。
    -   **讀音反查**: 以 `;;` 開頭。
    -   **自定義造詞**: 以 `;` 開頭。

## 開發與貢獻
-   **修改詞庫**: 可直接在 `liur_customWords.dict.yaml` 新增詞彙。
-   **調整功能**: 建議透過 `liur.custom.yaml` 進行覆蓋設定，以維持原始設定檔的整潔。
