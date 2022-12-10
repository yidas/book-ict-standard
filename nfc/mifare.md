# MIFARE 門禁卡/磁扣應用

## Spec

- [硬體架構及工作原理](https://zh.wikipedia.org/wiki/MIFARE#%E7%A1%AC%E9%AB%94%E6%9E%B6%E6%A7%8B%E5%8F%8A%E5%B7%A5%E4%BD%9C%E5%8E%9F%E7%90%86)

### Sector 0 - Block 0

|Byte|Length|Content|
|---|---|---|
|1|4|UID|
|5|1|bit count check|
|6|1|SAK (08:一般加密卡, 28:特殊加密卡如銀行卡)|
