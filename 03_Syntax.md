# KUKA Robot Language（KRL）

## WorkVisual

WorkVisual是KUKA機器人的程式端開發環境

- Workvisual 5.0啟動畫面

![Image](./img/KRL/Workvisual_5.0_cover.jpg)

## KRL教學

KRL程式分為.src與.dat兩個檔案，.src描述了程式的動作，.dat存放著.src中所需要用到的程式變數。可在WorkVisual中的Project Structure欄位新增.src與.dat檔案到專案內，或是透過匯入的方式將已寫好的檔案加入WorkVisual專案中

- 新增.src與.dat檔案

![Image](./img/KRL/KRL_CreateSRCfile.gif)

- WorkVisaul中一段自動生成的程式碼

![Image](./img/KRL/KRL_BasisCode.jpg)

在KRL中，程式碼會由數個DEF-END或是DEFFCT-ENDFCT的區塊構成

### 命名變數

在KRL中的命名受到以下規範：

- **最長**僅能24個字元
- **僅能使用**26個英文字母（A-Z）、10個數字（0-9）與2個特殊字元「_」、「$」
- 命名時第一個字元**不能**使用數字
- 命名時**不能**使用關鍵字

### 宣告變數

在KRL中的宣告受到以下規範

- 在.src檔中宣告變數時，需要宣告在DEF與INI之間的區域，並在INI之後賦予初始值
- 變數可以宣告為區域變數或是全域變數（GLOBAL）

語法
```
DECL Data_Type Variable_Name
```

範例

1. 在.src檔中
```
DEF DefineValueExample
    DECL INT Counter
    INI
    Counter = 5
END
```

2. 在.dat檔中
```
DEFDAT DefineValueExample
    DECL INT Counter = 5
ENDDAT
```
