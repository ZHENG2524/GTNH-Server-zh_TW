# GTNH 伺服器端繁體中文（台灣）訊息補丁

給 GT: New Horizons 伺服器管理員用。客戶端語言包請見 [GTNH-Translations-zh_TW](https://github.com/ZHENG2524/GTNH-Translations-zh_TW)。

## 為什麼需要
連線到伺服器時，歡迎訊息、魔法護盾等提示是**伺服器**用英文產生、再以純文字傳給玩家，客戶端語言包改不了。伺服器只讀 jar 內的 `en_US.lang`，所以要改伺服器 `mods` 資料夾裡的 jar。

## 涵蓋範圍
| jar | 檔案 | 內容 |
|---|---|---|
| `GTNewHorizonsCoreMod-*.jar` | `assets/dreamcraft/lang/en_US.lang` | 8 條歡迎訊息 |
| `YAMCore-*.jar` | `assets/yamcore/lang/en_US.lang` | 2 條魔法護盾訊息 |

以 GTNH 2.8.4（CoreMod 2.7.268、YAMCore 0.7.1）測試。

## 使用
```bash
python3 tools/patch_server_jars.py <伺服器 mods 資料夾> <輸出資料夾>
```
原檔不會被修改。請先備份原 jar，再把輸出的 jar 換進 `mods`，重啟伺服器。若伺服器正在執行，請用改名覆蓋（`mv`）而不是直接複製覆蓋。

## 翻譯品質
本倉庫的譯文為人工撰寫的少量訊息，尚未經過其他玩家校對。發現錯誤請開 issue。

## 授權
翻譯內容以 [CC BY-NC-SA 4.0](LICENSE) 釋出，與 GT New Horizons 模組包一致。原文著作權屬 GTNH 團隊及各模組作者；本專案不含任何模組 jar。
