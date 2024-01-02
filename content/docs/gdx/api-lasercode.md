+++
title = "แนวทางการพัฒนาระบบโดยใช้ API Laser Code"
weight = 16
+++

### ขั้นตอนการเรียก API
  
ลงทะเบียนใช้งาน API [ดาวน์โหลดแบบฟอร์ม](/files/FM-C17-016-Rev.2-GDX.pdf) ลงนามและแสกนส่งที่ e-mail contact@dga.or.th

### ขั้นตอนการพัฒนา

* ขั้นที่ 1 : ทำการขอ Token จาก Consumer-Key ที่ได้รับจากการลงทะเบียนกับ สพร.

* ขั้นที่ 2 : นำ Token ที่ได้มาเรียก API Laser Code

#### ขั้นที่ 1 : การขอ Token
  
การเรียกใช้งานข้อมูลผ่าน Government API มี 2 ขั้นตอน ตัวอย่าง Source Code ดังนี้ [คลิกเพื่อดูรายละเอียด] 

| หัวข้อ | รายละเอียด |
| --- | --- |
| API | https://api.egov.go.th/ws/auth/validate?ConsumerSecret=[Secret]&AgentID=[เลขประจำตัวประชาชน] |
| Method | GET |

**Request Parameters**

| รายการข้อมูล | รายละเอียด |
| --- | --- |
| ConsumerSecret | เช่น ConsumerSecret=xxxxxxxxxxxxxx |
| AgentID | เลขประจำตัวประชาชน 13 หลัก เช่น AgentID=1234567890123 หรือ ชื่อระบบภาษาอังกฤษ |

**Request Header**

| รายการข้อมูล | รายละเอียด |
| --- | --- |
| Consumer-Key | Consumer-Key ที่ได้ลงทะเบียนกับ สพร. (ระบบส่งให้ทาง e-Mail ที่ลงทะเบียนไว้) |
| Content-Type | กำหนดค่าดังนี้ : application/x-www-form-urlencoded; charset=utf-8 |

**Response**

```
BODY
{
"Result": "8e1ac089-0000-aaaa-0000-403c0c9ab867"
}
```

**Response Parameters**

| รายการข้อมูล | รายละเอียด |
| --- | --- |
| Result | Token String สำหรับใช้ในการเรียก API ต่างๆ |

หลังจากที่ Validate เรียบร้อยแล้ว กรณีที่ไม่มีการเรียกใช้งาน API ใด ๆ Token มีอายุ 60 นาที

#### ขั้นที่ 2 : การเรียก API Laser Code

| หัวข้อ | รายละเอียด |
| --- | --- |  
| API | https://api.egov.go.th/ws/dopa/verification/personal?CitizenID=CitizenID&FirstName=FirstName&LastName=LastName&BEBirthDate=BEBirthDate&LaserCode=LaserCode |
| Method | GET |

API Spec : https://gdx.dga.or.th/DataCatalog/Dictionary/Detail?id=4996ceda-33a8-49ad-9841-e169fc9ecc4a

**Request Parameters**

| รายการข้อมูล | รายละเอียด |
| --- | --- |
| CitizenID | หมายเลขบัตรประจำตัวประชาชน 13 หลักของบุคคลที่ต้องการตรวจสอบข้อมูล |
| FirstName | ชื่อจริง (ภาษาไทย) ไม่ต้องใส่คำนำหน้า |
| | กรณีมีชื่อกลาง ไม่ต้องใส่ข้อมูล |
| LastName | นามสกุล (ภาษาไทย) |
| BEBirthDate | วัน-เดือน-ปี พ.ศ. เกิด มีรูปแบบเป็น YYYYMMDD เช่น 25381229 <br /> กรณีหน้าบัตรประจำตัวประชาชนไม่ระบุ วัน, เดือน หรือ ปี ให้ใส่ค่า 0 เช่น 25380000 |
| LaserCode | หมายเลขหลังบัตรประจำตัวประชาชน 12 หลัก (พิมพ์ติดกันไม่ต้องใส่ "-") เช่น JT1234567890 <br /> หลักที่ 1-2 เป็นตัวอักษรภาษาอังกฤษ และหลักที่ 3-12 เป็นตัวเลข <br />(Laser Code Spec : https://stat.bora.dopa.go.th/card/smartcard4_5.htm ) |

**Request Header**

| รายการข้อมูล | รายละเอียด |
| --- | --- |
| Consumer-Key | Consumer-Key ที่ได้ลงทะเบียนกับ สพร. (ระบบส่งให้ทาง e-Mail ที่ลงทะเบียนไว้) |
| Content-Type | กำหนดค่าดังนี้ : application/x-www-form-urlencoded; charset=utf-8 |

**Response**

```
BODY{
    "Result": true
}
```

หรือ

```
BODY {
    "Result": false
}
```
 
**Response Parameters**

| รายการข้อมูล | รายละเอียด |
| --- | --- |
| Result | True หรือ False |

ตัวอย่างการเรียก API Laser Code

### Response Code
  
API Laser Code ถ้าเรียกสำเร็จจะได้ status 200
 
หากได้ status 500 ต้องดู body ดังนี้

| Code | Message | หมายเหตุ |
| --- | --- | --- |
| [2] | บัตรสิ้นสภาพการใช้งาน เนื่องจากกรณี การเปลี่ยนที่อยู่ | |
| [4] | สถานะไม่ปกติ => ไม่พบเลข Laser จาก PID นี้ | กรณีกรอก Laser Code ผิด |
| [4] | สถานะไม่ปกติ => ข้อมูลไม่ตรง | กรณีกรอก ชื่อ นามสกุล หรือ วัน-เดือน-ปี เกิด ผิด |
 
 
### FAQ
  
กรณีใช้บัตรประจำตัวประชาชน รุ่นตลอดชีพ ที่ไม่เป็น smart card จะไม่มีรหัส Laser Code หลังบัตรจึงไม่สามารถใช้งานได้
