# MIFARE 門禁卡/磁扣應用

## 感應卡

[感應卡(Proximity card)](https://zh.wikipedia.org/zh-tw/%E6%84%9F%E5%BA%94%E5%8D%A1)適用於[ISO/IEC 14443](https://zh.wikipedia.org/zh-tw/ISO/IEC_14443)標準與ISO/IEC 15693標準。它也可以用來指那些使用125 kHz或13.56 MHz的非接觸型RFID感應卡，這些技術通常被使用於非接觸型智慧卡之上。

|Standard|Frequency|Common Name|Example|
|---|---|---|---|
|[EM](https://en.wikipedia.org/wiki/EM_Microelectronic)|125kHz|Proximity card/EM卡/ID卡|簡易門禁感應卡磁扣|
|[MIFARE](https://zh.wikipedia.org/wiki/MIFARE)|13.56MHZ|MIFARE卡/IC卡|悠遊卡/銀行卡|

---

## Spec

- [硬體架構及工作原理](https://zh.wikipedia.org/wiki/MIFARE#%E7%A1%AC%E9%AB%94%E6%9E%B6%E6%A7%8B%E5%8F%8A%E5%B7%A5%E4%BD%9C%E5%8E%9F%E7%90%86)

### Sector 0 - Block 0

每張卡片第一區段的第一區塊（sector 0，block 0）只能讀取無法寫入資料，稱為製造商代碼（Manufacturer Code）

Classic with 4 UID:

|Byte|Length|Content|
|---|---|---|
|0|4|UID|
|4|1|bit count check|
|5|1|SAK (08:一般加密卡, 28:特殊加密卡如銀行卡)|

---

## Crack 破解與複製

讀寫部分需要裝置晶片(如[ACR122U](https://wiki.archlinux.org/title/Touchatag_RFID_Reader))支援，Read來說一般手機NFC晶片可能只能讀製造商代碼（Manufacturer Code）block，如使用[MifareClassicTool](https://github.com/ikarus23/MifareClassicTool)全掃sector內容最終皆失敗狀況
