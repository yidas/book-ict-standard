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

## 讀卡機驗證原理

卡機三重認證步驟：
1. 卡片產生一個亂數RB傳送到讀卡機。
2. 讀卡機會將接收到的亂數RB依公式加密編碼後的TokenAB數值並傳送回卡片。
3. 卡片接 收到TokenAB後，會把加密部份解譯出來然後比對參數B、亂數RB。同時並依據收到的亂數RA，參照公式編碼後產生TokenBA傳送回讀卡機。
4. 讀卡機接收到TokenBA後，又把加密過的部份解譯，比較亂數RB，RA與TokenBA中解出之RB、RA是否相符，正確的就可以完成指令（扣款、打 開門鎖或是登記其他事項）。

> [複製一張宿舍門禁卡(三) 操作存取卡片流程 - AndyWu's Notes](https://notes.andywu.tw/2018/%E8%A4%87%E8%A3%BD%E4%B8%80%E5%BC%B5%E5%AE%BF%E8%88%8D%E9%96%80%E7%A6%81%E5%8D%A1%E4%B8%89-%E6%93%8D%E4%BD%9C%E5%AD%98%E5%8F%96%E5%8D%A1%E7%89%87%E6%B5%81%E7%A8%8B/)

---

## Crack 破解與複製

讀寫部分需要裝置晶片(如[ACR122U](https://wiki.archlinux.org/title/Touchatag_RFID_Reader))支援，手機app可使用如[MifareClassicTool](https://github.com/ikarus23/MifareClassicTool)利用Key Brute attack掃出Sector內容

> [MIFARE系列7《安全性》- 壹讀](https://read01.com/J06JPK.html#.Y5VYxXZBybg)
