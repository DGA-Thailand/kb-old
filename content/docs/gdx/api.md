+++
title = "แนวทางการพัฒนาระบบโดยใช้ API (สำหรับผู้พัฒนาหน่วยงาน)"
weight = 15
+++

### คุณลักษณะการใช้งานผ่าน Application Program Interface (API)

หากหน่วยงานท่านมีระบบการให้บริการผ่านช่องทางออนไลน์ (e-Service) หรือระบบสนับสนุนการให้บริการ (Backend) อยู่แล้ว และต้องการเชื่อมโยงข้อมูลต่างๆ ขั้นต้นกับระบบของหน่วยงานท่าน ท่านสามารถเชื่อมโยงข้อมูลต่างๆ ผ่าน Application Program Interface (API) ได้ โดย API ดังกล่าว ใช้มาตรฐานต่างๆ ดังนี้

* ใช้โปรโตคอล RESTful Web Service (ดูรายละเอียดเพิ่มเติมที่ https://en.wikipedia.org/wiki/Representational_state_transfer)
* รักษาความปลอดภัยในการรับส่งข้อมูลด้วย HTTPS (ดูรายละเอียดเพิ่มเติมที่ https://en.wikipedia.org/wiki/HTTPS)
* ใช้ข้อมูลในรูปแบบของ JSON (Javascript Object Notation) เป็นหลัก ทั้งในคำขอ (Request) และคำตอบกลับข้อมูล (Response)
* ข้อความต่างๆ (text) ใช้ Unicode Transformation Format (UTF-8)
* ข้อมูลที่เป็นไฟล์แนบ หรือภาพ (Binary Data) ให้เข้ารหัสในรูปแบบ Base 64 Encoding (https://en.wikipedia.org/wiki/Base64)
* สถานภาพของการร้องขอ (Response Code) อ้างอิงได้จากสถานภาพของโปรโตคอล HTTP เช่น
    * Status Code = 200 หมายถึง การร้องขอที่สำเร็จ
    * Status Code = 401 หมายถึง ท่านไม่มีสิทธิในการเรียกดูข้อมูลดังกล่าว
    * Status Code = 404 หมายถึง ไม่มีข้อมูลดังกล่าว 

ดู Status Code ทั้งหมดได้ที่นี่ [คลิกเพื่อเปิดดูรายละเอียด](https://th.wikipedia.org/wiki/%E0%B8%A3%E0%B8%B2%E0%B8%A2%E0%B8%8A%E0%B8%B7%E0%B9%88%E0%B8%AD%E0%B8%A3%E0%B8%AB%E0%B8%B1%E0%B8%AA%E0%B8%AA%E0%B8%96%E0%B8%B2%E0%B8%99%E0%B8%A0%E0%B8%B2%E0%B8%9E%E0%B8%82%E0%B8%AD%E0%B8%87%E0%B9%80%E0%B8%AD%E0%B8%8A%E0%B8%97%E0%B8%B5%E0%B8%97%E0%B8%B5%E0%B8%9E%E0%B8%B5)

### ขั้นตอนการเรียกใช้ข้อมูลผ่าน API
  
หน่วยงานจำเป็นจะต้องยืนยันผู้ใช้งานในขั้นตอนการเรียกใช้บริการ Government API สำหรับการขอใช้บริการข้อมูลต่าง ๆ โดยจำเป็นจะต้องระบุตัวแปร ดังนี้

| Parameter | Required | Description |
| --- | --- | --- |
| Consumer-Key | Required | เป็นชุดรหัสที่ สพร. ออกให้ เพื่อความปลอดภัยในการเรียกใช้งาน API |
| ConsumerSecret | Required | เป็นชุดรหัสที่ สพร. ออกให้ เพื่อความปลอดภัยในการเรียกใช้งาน API |

* แอพพลิเคชั่นหนึ่งๆ ของหน่วยงานจะใช้ Consumer-Key และ ConsumerSecret ในการ Validation เพื่อเรียกใช้งาน API ได้ (เปรียบเสมือน User Name และ Password ของแอพพลิเคชั่นหนึ่งๆ)
* ผู้ดูแลระบบของหน่วยงานสามารถลงทะเบียนการขอใช้ API ข้อมูล และขอ Consumer-Key, ConsumerSecret กับ สพร. ได้ที่สอบถามรายละเอียดเพิ่มเติมได้ที่ contact@dga.or.th หรือ โทร. 0-2612-6060
 
การเรียกใช้งานข้อมูลผ่าน Government API มี 2 ขั้นตอน ดังนี้

#### ขั้นตอนที่ 1 Government API Validation

API

```
https://api.egov.go.th/ws/auth/validate?ConsumerSecret=[Secret]&AgentID=[เลขประจำตัวประชาชน]
```

ทำการ Validate ส่วนของ Consumer-Key และ ConsumerSecret เพื่อขอ Token และเปิด Session ในการเรียกใช้ Service โดยสามารถดูรายละเอียด API และ Response Code ได้ที่

https://app.swaggerhub.com/apis/dga/Validate/1.0

**หมายเหตุ** หลังจากที่ Validate เรียบร้อยแล้ว กรณีที่ไม่มีการเรียกใช้งาน API ใด ๆ Token มีอายุ 60 นาที
AgentID เป็นเลขประจำตัวประชาชน 13 หลักของผู้ใช้งาน(นำมาจากฐานข้อมูล User ระบบของหน่วยงาน)  สำหรับไว้อ้างอิง log การเรียกใช้งานข้อมูลกับ Consumer-Key ที่ทางหน่วยงานลงทะเบียนไว้
 
#### ขั้นตอนที่ 2 ทำการเรียกใช้ข้อมูล API

โดยเรียก HTTP Request วิธี GET และต้องทำการฝัง HEADER ดังนี้

| Parameter | Value |
| --- | --- |
| Content-Type | application/x-www-form-urlencoded |
| Consumer-Key | ชุดรหัสที่ สพร. ออกให้ |
| Token | TOKEN ที่ได้รับกลับมาจาก สพร. ในการ Validate ข้างต้น |

### การขอ Token
  
การเรียกใช้งานข้อมูลผ่าน Government API มี 2 ขั้นตอน ตัวอย่าง Source Code ดังนี้ [คลิกเพื่อดูรายละเอียด] 

{{< tabs "การดาวนโหลด" >}}
{{< tab "API [Production]" >}}
https://api.egov.go.th/ws/auth/validate?ConsumerSecret=[Secret]&AgentID=[เลขประจำตัวประชาชน]
{{< /tab >}}
{{< tab "API [TEST]" >}}
https://trial.dga.or.th/ws/auth/validate?ConsumerSecret=[Secret]&AgentID=[เลขประจำตัวประชาชน]
{{< /tab >}}
{{< tab "Methed" >}}
GET
{{< /tab >}}
{{< /tabs >}}

**Request Parameters**

| รายการข้อมูล | รายละเอียด |
| --- | --- |
| ConsumerSecret | เช่น ConsumerSecret=xxxxxxxxxxxxxx |
| AgentID | เลขประจำตัวประชาชน 13 หลัก เช่น AgentID=1234567890123 หรือ ชื่อระบบภาษาอังกฤษ <br/> กรณีเรียก API Personal Signing ต้องกำหนด AgentID เป็นเลขประจำตัวประชาชนของผู้เซ็นเอกสารเท่านั้น |

**Request Header**

| รายการข้อมูล | รายละเอียด |
| --- | --- |
| Consumer-Key | Consumer-Key ที่ได้ลงทะเบียนกับ สพร. (ระบบส่งให้ทาง e-Mail ที่ลงทะเบียนไว้) |
| Content-Type | กำหนดค่าดังนี้ : application/x-www-form-urlencoded; charset=utf-8 |

**Response**

```JSON
{
"Result": "8e1ac089-0000-aaaa-0000-403c0c9ab867"
}
```

**Response Parameters**

| รายการข้อมูล | รายละเอียด |
| --- | --- |
| Result | Token String สำหรับใช้ในการเรียก API ต่างๆ <br />(กรณีขอ Token ไม่สำเร็จ หรือ error อื่นๆ ให้ทำการเรียก API ใหม่อีกครั้ง จนกว่าจะได้ Token ไปใช้เรียกเรียกร่วมกับ API อื่นๆ) |

#### รายการ API และตัวอย่าง Source Code ภาษาต่างๆ
  
หากหน่วยงานท่านมีระบบการให้บริการผ่านช่องทางออนไลน์ (e-Service) หรือระบบสนับสนุนการให้บริการ (Backend) อยู่แล้ว และต้องการเชื่อมโยงข้อมูลต่างๆ ขั้นต้นกับระบบของหน่วยงานท่าน ท่านสามารถเชื่อมโยงข้อมูลต่างๆ ผ่าน Application Program Interface (API) ได้ โดยมีรายละเอียด และตัวอย่างวิธีการเรียกใช้ข้อมูลตามข้างล่าง

* ท่านสามารถดูรายละเอียด API ข้อมูลบุคคล, นิติบุคคล หรือของหน่วยงานต่างๆ ได้ที่ https://app.swaggerhub.com/apis/dga
* ตัวอย่าง Source Code วิธีการเรียกใช้ API เพื่อเชื่อมโยงข้อมูลจากบัตรประชาชนแบบ Smart Card หรือจากระบบฐานข้อมูลของหน่วยงานต่างๆ ที่เกี่ยวข้อง https://sc.dga.or.th/tutorials
* ตัวอย่าง Source Code C# การ Decode จาก Base 64(url safe format) เป็น PDF [คลิกเพื่อดาวน์โหลด]

#### คู่มือการพัฒนาระบบเพื่อใช้งาน API
  
* ข้อมูลบุคคล Linkage Center [คลิกเพื่อดูรายละเอียด API]
* ข้อมูลบุคคล IKNO [คลิกเพื่อเปิดดูเอกสาร](/files/GovAPI_PersonAPI_AdminManual_22112018.pdf) (เปลี่ยนไปใช้งานแบบ Linkage Center แทน)
* ข้อมูลนิติบุคคล [คลิกดูรายละเอียด API]

#### การพัฒนาระบบข้อมูลบุคคล Linkage API โดยใช้สิทธิ์เจ้าหน้าที่ และสิทธิ์ประชาชน
  
ขั้นตอนการเรียกใช้ API ข้อมูลบุคคล Linkage โดยใช้สิทธิ์ประชาชน จะเหมือนการพัฒนาโดยใช้สิทธิ์เจ้าหน้าที่ทุกขั้นตอน แต่จะต่างกันตอนเรียกใช้งานเท่านั้น(ที่ต้องเสียบบัตรของประชาชนผู้รับบริการเพิ่ม) โดยทำตาม 2 ขั้นตอน เช่นที่กล่าวไว้ในหัวข้อ "ขั้นตอนการเรียกใช้ข้อมูลผ่าน API" และมีรายละเอียดเพิ่มเติม ดังนี้

เจ้าหน้าที่ต้องเสียบบัตร login GovAMI ก่อนเรียก API ข้อมูล [วิธีการใช้งานโปรแกรม GovAMI]

**ขั้นตอนที่ 1 Government API Validation**

เลขประจำตัวประชาชนที่กำหนดให้กับตัวแปร AgentID ต้องเป็นเลขเดียวกับเลขประจำตัวประชาชนของบัตรเจ้าหน้าที่ที่เสียบ login GovAMI เท่านั้น

**ขั้นตอนที่ 2 ทำการเรียกใช้ข้อมูล API**

ทำการเรียกขอข้อมูล จาก API Linkage ต้องทําการเรียกผ่าน Url และ Parameter ดังน้ี

[คลิกเพื่อดูตัวอย่าง Source Code] หรือ [คลิกเพื่อเปิดดูเอกสาร pdf]

| วิธีการ | GET |
| --- | --- |
| URL | https://api.egov.go.th/ws/dopa/linkage/v1/link?OfficeID=<OfficeID>&ServiceID=<ServiceID>&Version=<Version>&CitizenID=<CitizenID> |

| Parameter | Required | Type | Description |
| OfficeID | Required |String |หมายเลขหน่วยงานผู้ให้บริการข้อมูล |
| ServiceID | Required | String | หมายเลขชุดข้อมูล
| Version | Required | String | เวอร์ชันชุดข้อมูล |
| CitizenID | Required | String | หมายเลขบัตรประจําตัวประชาชน 13 หลัก ของบุคคลที่ต้องการทราบข้อมูล |

OfficeID, ServiceID และ Version สามารถดูได้จาก https://linkagemgmt.bora.dopa.go.th/#/
กรณีสิทธิ์ประชาชน เลขประจำตัวประชาชนของผู้รับบริการที่ค้นหาข้อมูล ต้องเป็นเลขเดียวกับเลขประจำตัวประชาชนของบัตรผู้รับบริการที่เสียบ GovAMI ในกรอบผู้รับบริการเท่านั้น

#### ตัวอย่างการทดสอบเรียกใช้ API จาก Restlet Client ของ Chrome Extension
  
ติดตั้ง R-Client โดยใช้ Chrome browser ที่ https://chrome.google.com/webstore/detail/restlet-client-rest-api-t/aejoelaoggembcahagimdiliamlcdmfm?hl=en

**ขั้นตอนที่ 1** Government API Validation

![API Validation Step](/images/gdx/gdx-api-3-chrome.png)

**ขั้นตอนที่ 2** ทำการเรียกใช้ข้อมูล API

![API Data Request](/images/gdx/gdx-api-5-chrome.png)

![API Data Response](/images/gdx/gdx-api-6-chrome.png)

![API Data Response](/images/gdx/gdx-api-7-chrome.png)

โดยนำ Token ที่ได้มาแนบที่ Headers (Method : Get)