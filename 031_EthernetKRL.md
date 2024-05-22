---
title: KUKA EthernetKRL
---

<style>
    .stress
    {
        color:#FF0000;
    }
    .keyWords
    {
        color:#00E3E3;
    }
    .keyPoint
    {
        color:#ff0000;
    }
</style>

# KUKA EthernetKRL（EKI）

EKI是KUKA機器手臂的選配套件，用於透過乙太網路與外部連接的系統進行資料的交換

特點

- 透過KUKA Line Interface（KLI）連接
- 使用TCP/IP通訊協定
- 可同時與16個外部系統交換資料
- 使用XML格式傳輸資料
- 可自定義Server/Client
- 可定義「事件訊息」（監控$FLAG或輸出$OUT）

進階話題
- [XML介紹(維基百科)](https://zh.wikipedia.org/zh-tw/XML)
- [微軟-XML入門](https://support.microsoft.com/zh-tw/office/xml-%E5%85%A5%E9%96%80-a87d234d-4c2e-4409-9cbc-45e4eb857d44)
- [XML語法規則](https://www.ibm.com/docs/zh-tw/b2bis?topic=syntax-xml-rules)

# EKI程式

EKI使用XML文件定義基本的規範，並儲存在專案中Config/User/Common/EthernetKRL

XML格式以EthernetKRL作為最外層標籤，內部有三組標籤定義大部分的訊息

- Configuration
- Receive
- Send

## XML定義範例

Server範例

```xml
<ETHERNETKRL>
  <CONFIGURATION>
    <EXTERNAL>
      <TYPE>Client</TYPE>
    </EXTERNAL>
    <INTERNAL>
      <TYPE>Server</TYPE>
      <IP>192.168.1.147</IP>
      <PORT>54600</PORT>
      <ALIVE Set_Flag="1" />
      <ENVIRONMENT>Submit</ENVIRONMENT>
    </INTERNAL>
  </CONFIGURATION>
  <RECEIVE>
    <XML>
      <ELEMENT Tag="REQUEST/CMD" Type="INT" Set_Flag="2" />
      
	  <ELEMENT Tag="REQUEST/PARAMETERS" Type="INT" Set_Flag="3" />
	  <ELEMENT Tag="REQUEST/PARAMETERS/@VALUE" Type="INT" />
    </XML>
  </RECEIVE>
  <SEND>
    <XML>
      <ELEMENT Tag="RESPONSE/CMD" Type="INT" />
      <ELEMENT Tag="RESPONSE/CMD/@CODE" Type="INT" />
	  
	  <ELEMENT Tag="RESPONSE/PARAMETERS" Type="INT" />
	  <ELEMENT Tag="RESPONSE/PARAMETERS/@VALUE" Type="INT" />
    </XML>
  </SEND>
</ETHERNETKRL>
```

Client範例

```xml
<ETHERNETKRL>
  <CONFIGURATION>
    <EXTERNAL>
      <TYPE>Client</TYPE>
      <IP>192.168.1.100</IP>
      <PORT>54600</PORT>
      <ALIVE Set_Flag="1" />
    </EXTERNAL>
    <INTERNAL>
    </INTERNAL>
  </CONFIGURATION>
  <RECEIVE>
    <XML>
      <ELEMENT Tag="REQUEST/CMD" Type="INT" Set_Flag="2" />
      
	  <ELEMENT Tag="REQUEST/PARAMETERS" Type="INT" Set_Flag="3" />
	  <ELEMENT Tag="REQUEST/PARAMETERS/@VALUE" Type="INT" />
    </XML>
  </RECEIVE>
  <SEND>
    <XML>
      <ELEMENT Tag="RESPONSE/CMD" Type="INT" />
      <ELEMENT Tag="RESPONSE/CMD/@CODE" Type="INT" />
	  
	  <ELEMENT Tag="RESPONSE/PARAMETERS" Type="INT" />
	  <ELEMENT Tag="RESPONSE/PARAMETERS/@VALUE" Type="INT" />
    </XML>
  </SEND>
</ETHERNETKRL>
```

