<div align="center">

# 🖥️ GTNH 伺服器端繁體中文（台灣）訊息補丁

**GT: New Horizons · Server-side Traditional Chinese (Taiwan)**

讓伺服器傳送的歡迎訊息與魔法護盾提示，也能以熟悉的繁體中文呈現。

![Language](https://img.shields.io/badge/語言-繁體中文%20zh__TW-276749?style=for-the-badge)
![GTNH](https://img.shields.io/badge/測試版本-GTNH%202.8.4-2563eb?style=for-the-badge)
![Scope](https://img.shields.io/badge/補丁範圍-10%20條訊息-f59e0b?style=for-the-badge)

**[快速使用](#-快速使用)** · **[補丁範圍](#-補丁涵蓋範圍)** · **[客戶端語言包](https://github.com/ZHENG2524/GTNH-Translations-zh_TW)** · **[問題回報](../../issues)**

</div>

> [!IMPORTANT]
> **本專案供 GTNH 伺服器管理員使用，不是一般玩家的客戶端語言包。** 修改的是伺服器模組 JAR 裡實際被讀取的英文語言資源；請先備份、停服再替換。不同版本的模組不保證相容。

## ✨ 補丁亮點

| 功能 | 涵蓋訊息 | 適用模組 |
| :--- | ---: | :--- |
| 👋 伺服器歡迎、任務書與社群連結提示 | **8 條** | GTNewHorizonsCoreMod |
| 🛡️ 魔法護盾出現／消失提示 | **2 條** | YAMCore |
| 📦 修補方式 | **產生新的 JAR** | 保留來源檔案 |
| 🎮 已記錄測試基準 | **GTNH 2.8.4** | CoreMod 2.7.268 / YAMCore 0.7.1 |

> [!NOTE]
> 上表是**工具內已定義的 10 個翻譯鍵**，不代表能翻譯伺服器產生的所有英文訊息。此處列出的版本為現有專案紀錄中的測試基準，不代表本次 README 美化重新完成遊戲實測。

## ❔ 為什麼還需要伺服器補丁？

有些訊息由**伺服器**直接產生英文純文字，再傳送給玩家。玩家即使已安裝繁體中文語言包，這些文字也不會因客戶端語言設定而自動翻譯。

本補丁透過修改特定模組 JAR 內的 `en_US.lang` 對應條目，讓伺服器產生指定訊息時使用繁體中文。

| 想翻譯的內容 | 請使用 |
| --- | --- |
| 物品、機器、材料、任務與客戶端介面 | 🌏 **[GTNH 繁體中文（台灣）語言包](https://github.com/ZHENG2524/GTNH-Translations-zh_TW)** |
| 伺服器送出的歡迎訊息、魔法護盾訊息 | 🖥️ **本專案** |

## 📦 快速使用

### 1. 下載並準備

下載本專案原始碼，確認電腦具備 Python 3，並找到**伺服器**的 `mods` 資料夾。請先備份原始模組 JAR 與重要伺服器資料。

### 2. 產生修補檔

在專案根目錄執行：

```bash
python3 tools/patch_server_jars.py "<伺服器 mods 資料夾>" "<輸出資料夾>"
```

例如（將路徑換成你的實際位置）：

```bash
python3 tools/patch_server_jars.py "/srv/gtnh/mods" "./patched-jars"
```

腳本會搜尋 `GTNewHorizonsCoreMod*.jar` 與 `YAMCore*.jar`，並在指定輸出目錄產生修補後的 JAR；**來源 JAR 不會被就地修改**。

### 3. 停服、替換、重啟

1. **先停止伺服器**，確定已備份原始 JAR。
2. 檢查輸出目錄確實產生了預期的 JAR；沒有輸出時先確認檔名與版本，不要繼續。
3. 將修補後的 JAR 放回伺服器 `mods`，取代對應原檔；**同一模組不要留下新舊兩份 JAR**。
4. 重新啟動伺服器，在遊戲內檢查歡迎訊息與護盾提示。

> [!CAUTION]
> **不要在伺服器運作時直接覆蓋正在使用的 JAR。** 腳本目前依檔名前綴尋找模組，未強制限制版號，也不會自動證明每個目標翻譯鍵都存在。請在替換前自行核對 JAR 名稱與內容。若出現啟動失敗或提示異常，停服並還原備份。

## 🧩 補丁涵蓋範圍

| 模組 JAR | 內部語言資源 | 翻譯內容 |
| --- | --- | --- |
| `GTNewHorizonsCoreMod-*.jar` | `assets/dreamcraft/lang/en_US.lang` | 8 條歡迎、任務書、Wiki、GitHub、Discord 提示 |
| `YAMCore-*.jar` | `assets/yamcore/lang/en_US.lang` | 2 條魔法護盾提示 |

可在 [`tools/patch_server_jars.py`](tools/patch_server_jars.py) 檢視完整對應鍵與翻譯文字。補丁僅替換指定語言條目，不以修改遊戲機制為目的。

## 🤝 翻譯品質與問題回報

目前 10 條訊息由人工撰寫，**尚未經其他玩家全面校對**。歡迎在 [GitHub Issues](../../issues) 回報問題，附上 GTNH／模組版本、出現問題的畫面、原文及建議繁體譯法。

本專案是非官方社群補丁，與 GTNH 團隊及各模組作者沒有官方從屬關係。

## 📜 來源與授權

翻譯內容依本倉庫的 [GPL-3.0 授權](LICENSE) 提供。原始程式與文字之權利仍歸 GTNH 團隊和相應模組作者所有；**本倉庫不提供任何模組 JAR**。使用修補檔時仍應遵守來源模組的授權規定。

---

<div align="center">

**🌏 [客戶端繁體中文語言包](https://github.com/ZHENG2524/GTNH-Translations-zh_TW)** · **🖥️ 伺服器端訊息補丁** · **💬 [回報問題](../../issues)**

讓 GTNH 的繁體中文體驗，一點一點更完整。

</div>
