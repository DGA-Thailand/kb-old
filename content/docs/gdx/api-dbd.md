+++
title = "ข้อมูลบุคคลนิติบุคคล กรมพัฒนาธุรกิจการค้า (DBD)"
weight = 18
+++

รายละเอียด Web Service ข้อมูลนิติบุคคล (Data Dictionary) ประกอบด้วย ข้อมูลนิติบุคคล, ข้อมูลและหน้าเอกสารผู้ถือหุ้น, ข้อมูลงบการเงิน, ข้อมูลและหน้าเอกสารหนังสือบริคณห์สนธิ และเอกสารประกอบ, ข้อมูลวัตถุประสงค์, ข้อมูลทะเบียนพาณิชย์, ข้อมูลการประกอบธุรกิจของคนต่างด้าว, ข้อมูลทะเบียนหลักประกันธุรกิจ

### [DBD-001-04] API ข้อมูลทะเบียนนิติบุคคล (แบบข้อความ) (text)

| รายการข้อมูล | รายละเอียด |
| --- | --- |
| API | https://api.egov.go.th/ws/dbd/juristic/v4/profile/information?JuristicID=[JuristicID]

JuristicID คือ เลขทะเบียนนิติบุคคล

**Response**
```
BODY
{
"ResultList":[
{
"JuristicType": "5",
"JuristicID": "0000000000000",
"OldJuristicID": null,
"RegisterDate": "25620829",
"JuristicName_TH": "ทดสอบ จำกัด",
"JuristicName_EN": "TEST COMPANY",
"RegisterCapital": "5000000",
"PaidRegisterCapital": "5000000",
"NumberOfObjective": "22",
"NumberOfPageOfObjective": "1",
"JuristicStatus": "ยังดำเนินกิจการอยู่",
"StandardID": "41002",
"CommitteeInformations":[
{
"Sequence": 1,
"FirstName": "ทดสอบ",
"LastName": "ข้อมูล",
"Title": "นาย",
"Type": "K"
}
],
"AuthorizeDescriptions":[
{
"Sequence": 2,
"AuthorizeDescription": "และประทับตราสำคัญของบริษัท",
"Type": "L"
}
],
"StandardObjectives":[
{
"Sequence": null,
"ObjectiveDescription": "ประกอบกิจการรับเหมาก่อสร้างอาคาร ที่พักอาศัย"
}
],
"AddressInformations":[
{
"Sequence": null,
"AddressName": "สำนักงานใหญ่",
"FullAddress": "123/1 ถ.พหลโยธิน",
"Building": null,
"RoomNo": null,
"Floor": null,
"VillageName": null,
"AddressNo": "123/1",
"Moo": null,
"Soi": null,
"Road": "พหลโยธิน",
"Tumbol": "จตุจักร",
"Ampur": "จตุจักร",
"Province": "กรุงเทพมหานคร",
"Phone": null,
"Email": null
}
]
}
],
"RawData": ""
}
```

**คำอธิบายชุดข้อมูล**

| รายการข้อมูล | รายละเอียด |
| --- | --- |
| JuristicType | ประเภทธุรกิจ<br />2=ห้างหุ้นส่วนสามัญ<br />3=ห้างหุ้นส่วน<br />5=บริษัทจำกัด<br />7=บริษัทจำกัดมหาชน |
| JuristicID | เลขทะเบียนนิติบุคคล |
| OldJuristicID | เลขทะเบียนนิติบุคคลเดิม |
| RegisterDate | วันที่จดทะเบียน ปี พ.ศ. เดือน วัน เช่น "25621021" |
| JuristicName_TH | ชื่อนิติบุคคล (ภาษาไทย) |
| JuristicName_EN | ชื่อนิติบุคคล (ภาษาอังกฤษ) |
| RegisterCapital | ทุนจดทะเบียน |
| PaidRegisterCapital | ทุนชำระแล้ว |
| NumberOfObjective	| จำนวนข้อวัตถุประสงค์ |
| NumberOfPageOfObjective | จำนวนแผ่นวัตถุประสงค์ | 
| JuristicStatus | สถานะนิติบุคคล เช่น ยังดำเนินกิจการอยู่ <br />พิทักษ์ทรัพย์เด็ดขาด <br />แปรสภาพ <br />เลิก(ไม่เสร็จการชำระบัญชี) <br />เลิก(เสร็จการชำระบัญชี) <br />ควบ <br />ถอน(บริคณห์) <br />ร้าง <br />ล้มละลาย |
| StandardID | รหัสธุรกิจ 5 หลัก (TSIC) |
| **CommitteeInformations** | |	 
| Sequence	| ลำดับ |
| FirstName | ชื่อกรรมการ/หุ้นส่วน |
| LastName | นามสกุลกรรมการ/หุ้นส่วน |
| Title	| คำนำหน้าชื่อ |
| Type | ประเภทกรรมการ<br />K=กรรมการหุ้นส่วน<br />L=หุ้นส่วนผู้จัดการ<br /><br />การนำไปใช้<br />- กรณีเป็นบริษัทจำกัด, บริษัทจำกัดมหาชน ในส่วนข้อมูลกรรมการ แสดงรายชื่อกรรมการหุ้นส่วน(K)<br />- กรณีเป็นห้างหุ้นส่วน, ห้างหุ้นส่วนสามัญ ในส่วนข้อมูลหุ้นส่วน แสดงรายชื่อหุ้นส่วน(K) และ หุ้นส่วนผู้จัดการ(L)
| **AuthorizeDescriptions** | | 	 
| Sequence | ลำดับ |
| AuthorizeDescription | รายละเอียด |
| Type | ประเภทข้อมูล<br />L=อำนาจกรรมการ<br />M=ข้อจำกัดอำนาจหุ้นส่วน<br />N=รายการอื่นที่เห็นสมควรทราบ<br />R=หมายเหตุการเปลี่ยนชื่อ<br />S=หมายเหตุอื่นๆ |
| **StandardObjectives** | |
| ObjectiveDescription | รายละเอียด TSIC |
| **AddressInformations** | |	 
| AddressName | สำนักงานใหญ่/ชื่อสาขา |
| FullAddress | ที่อยู่ |
| Building | อาคาร |
| RoomNo | เลขที่ห้อง |
| Floor | ชั้นที่ |
| VillageName | หมู่บ้าน |
| AddressNo | เลขที่บ้าน |
| Moo | หมู่ที่ |
| Soi | ตรอก/ซอย |
| Road | ถนน |
| Tumbol | ตำบล |
| Ampur | อำเภอ |
| Province | จังหวัด |
| Phone | เบอร์โทรศัพท์ |
| Email	| อีเมล |

RawData	ข้อมูลต้นฉบับ

#### 2 [DBD-002-04] API ข้อมูลทะเบียนนิติบุคคล (แบบข้อความในรูปแบบ pdf) (text-pdf) หรือหนังสือรับรองนิติบุคคล
  
| รายการข้อมูล | รายละเอียด |
| --- | --- |
| API https://api.egov.go.th/ws/dbd/juristic/v4/profile/information/pdf?JuristicID=[JuristicID] |

JuristicID คือ เลขทะเบียนนิติบุคคล

**Response**

```
BODY
{
"ID": "0000000000000",
"FileName": "0000000000000-ข้อมูลนิติบุคคล (V4)-Certificate_20191127130044.pdf",
"FileSize": "136581",
"mimeType": "application/pdf",
"Hashes": "328C8A716CE0956B3BF981F754953E9A",
"Result": "JVBERi0xLjcKJeLjz9MKMyAwIG9iago8PC9GVC9TaWcvVChT..."
}
```

**คำอธิบายชุดข้อมูล**

| รายการข้อมูล | รายละเอียด |
| --- | --- |
| ID | เลขทะเบียนนิติบุคคล |
| FileName | ชื่อไฟล์ |
| FileSize | ขนาดไฟล์ |
| mimeType | ประเภทไฟล์ |
| Hashes | แฮชไฟล์สำหรับตรวจสอบ |
| Result | ไฟล์ในรูปแบบ Base64 |

#### 3 [DBD-003-04] API บัญชีรายชื่อผู้ถือหุ้น (แบบข้อความ) (text)


API

``
https://api.egov.go.th/ws/dbd/juristic/v4/profile/shareholder?JuristicID=[JuristicID]
``

JuristicID คือ เลขทะเบียนนิติบุคคล
 
**Response**

```
BODY
{
"ResultList":[
{
"JuristicID": "0000000000000",
"ShareholderInfo":[
{
"JuristicName": "บจ.ทดสอบ เทค จำกัด",
"ParValue": "100",
"ReceiveDate": "2019-10-24 00:00:00.0",
"MeetingDate": "14/10/2562",
"SumOfHold": "50000"
}
],
"ShareholderDetail":[
{
"Title": "นาย",
"HolderName": "ชื่อ1",
"Lastname": "นามสกุล1",
"Career": "รับจ้าง",
"Nationality": "ไทย"
},
{
"Title": "นางสาว",
"HolderName": "ชื่อ2",
"Lastname": "นามสกุล2",
"Career": "รับจ้าง",
"Nationality": "ไทย"
}
]
}
],
"RawData": "PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZ..."
}
```
 
 **คำอธิบายชุดข้อมูล**

| รายการข้อมูล | คำอธิบาย |
| -- | -- |
| JuristicID | เลขนิติบุคคล |
| **ShareholderInfo** | | 
| JuristicName | ชื่อนิติบุคคล |
| ParValue | มูลค่าต่อหุ้น |
| ReceiveDate | วันที่รับเอกสาร |
| MeetingDate | วันที่ประชุม |
| SumOfHold | จำนวนหุ้นทั้งหมด |
| **ShareholderDetail** | | 
| Title | คำนำหน้าชื่อ |
| HolderName | ชื่อ |
| Lastname | นามสกุล |
| Career | อาชีพ |
| Nationality | สัญชาติ |
| RawData | ข้อมูลต้นฉบับ Base64 |

#### 4 [DBD-004-04] API บัญชีรายชื่อผู้ถือหุ้น (แบบข้อความในรูปแบบ pdf) (text-pdf)
  
API

```
https://api.egov.go.th/ws/dbd/juristic/v4/profile/shareholder/pdf?JuristicID=[JuristicID]
```

JuristicID คือ เลขทะเบียนนิติบุคคล
 
**Response**

```
BODY
{
"ID": "0000000000000",
"FileName": "0000000000000-ข้อมูลผู้ถือหุ้น (V4)-Certificate_20200225101416.pdf",
"FileSize": "250790",
"mimeType": "application/pdf",
"Hashes": "147EDBE0517818E5C886CC2C4CA4A096",
"Result": "JVBERi0xLjcKJeLjz9MKMyAwIG9iago8PC9GVC9TaWcvVC..."
}
```

**คำอธิบายชุดข้อมูล**

| รายการข้อมูล | คำอธิบาย |
| --- | --- |
| ID | เลขทะเบียนนิติบุคคล |
| FileName | ชื่อไฟล์ |
| FileSize | ขนาดไฟล์ |
| mimeType | ประเภทไฟล์ |
| Hashes | แฮชไฟล์สำหรับตรวจสอบ |
| Result | ไฟล์ในรูปแบบ Base64 |

#### 5 [DBD-005-04] API บัญชีรายชื่อผู้ถือหุ้น (แบบรูปภาพในรูปแบบ pdf) (image-pdf)
  
API

```
https://api.egov.go.th/ws/dbd/juristic/v4/profile/shareholder/image/pdf?JuristicID=[JuristicID]
```

JuristicID คือ เลขทะเบียนนิติบุคคล
 
**Response**

```
{
  "ID": "0000000000007",
  "FileName": "0000000000007-ข้อมูลผู้ถือหุ้น (V4) (รูปภาพ)-Certificate_20201028112450.pdf",
  "FileSize": "239235",
  "Info": {
    "Name": "ข้อมูลผู้ถือหุ้น (V4) (รูปภาพ)",
    "NumberOfPage": 2
  },
  "mimeType": "application/pdf",
  "Hashes": "D6ADCBFEEDF694781C21B89135442152",
  "Result": "JVBERi0xLjcKJeLjz9MKMyAwIG9iago8PC9GVC9TaWcvVChTaWduYXR1cmUxKS9WIDEgMCBSL0YgMTMyL....."
}
```

**คำอธิบายชุดข้อมูล**

| รายการข้อมูล | คำอธิบาย |
| -- | -- |
| ID | เลขนิติบุคคล |
| FileName |	ชื่อไฟล์ |
| FileSize |	ขนาดไฟล์ (Byte) |
| INFO | | 	 
| Name | ชื่อเอกสาร |
| NumberOfPage | จำนวนหน้าของเอกสาร |
| mimeType | ประเภทไฟล์ |
| Hashes | แฮชไฟล์สำหรับตรวจสอบ |
| Result | ไฟล์ในรูปแบบ Base64 |
#### 6 [DBD-006-04] API บัญชีรายชื่อผู้ถือหุ้น (แบบรูปภาพ) (image)
  
API

```
https://api.egov.go.th/ws/dbd/juristic/v4/profile/shareholder/image?JuristicID=[JuristicID]
```

JuristicID คือ เลขทะเบียนนิติบุคคล

**Response**

```
pretty 
{
"Type": "Shareholder",
"Page": 1,
"Contents":[
{
"Page": 0,
"Total": 1,
"Type": "application/pdf",
"Size": 82503,
"Data": "JVBERi0xLjQKJeLjz9MKMSAwIG9iago8PC9U..."
}
]
}
```

**คำอธิบายชุดข้อมูล**

| รายการข้อมูล | คำอธิบาย |
| -- | -- |
| Type | ประเภทข้อมูล (ข้อมูลชุดนี้คือ "Objective") |
| Page | จำนวนหน้าทั้งหมด |
| Contents | | 
| Page	| หน้าของข้อมูลที่แสดง (ข้อมูลชุดนี้จะแสดงทุกหน้า Page จึงเป็น 0 เท่านั้น) |
| Total	| จำนวนหน้าทั้งหมด(หน้า) |
| Type	| ประเภทไฟล์ |
| Size	| ขนาดไฟล์(byte) |
| Data | ไฟล์ในรูปแบบ Base64 |

#### 7 [DBD-007-04] API ข้อมูลงบการเงิน (แบบข้อความ) (text)
  
API

```
https://api.egov.go.th/ws/dbd/juristic/v4/profile/financial?JuristicID=[JuristicID]&Year=[Year]
```

JuristicID  คือ เลขทะเบียนนิติบุคคล
Year         คือ  ปี พ.ศ. ของงบการเงินที่ต้องการเรียกข้อมูล

**Response**

```
{
  "JuristicID": "01055491xxxxx",
  "RegisterCapital": "1000000",
  "AccountReceivable": "534221.5",
  "CurrentLiabilities": "1808906.67",
  "Inventory": null,
  "PaidUpCapital": "1000000",
  "ProperTREquipment": "697927.53",
  "ShareholderEquity": "1849525.68",
  "TotalAsset": "3658432.35",
  "TotalCurrentAsset": "2358504.82",
  "TotalLiabilities": "1808906.67",
  "AdminExpenses": "2278018.72",
  "CostOfGoodsSold": "7053862.58",
  "EarningPerShare": "14.26",
  "IncomeTax": null,
  "InterestExpenses": "100984.87",
  "NetProfit": "142562.96",
  "SaleRevenue": "9550028.05",
  "TotalRevenue": "9575429.13",
  "StatementYear": "2556"
}
```

**คำอธิบายชุดข้อมูล**

| รายการข้อมูล | คำอธิบาย |
| -- | -- |
| JuristicID | เลขทะเบียนนิติบุคคล |
| RegisterCapital | ทุนจดทะเบียน |
| AccountReceivable | ลูกหนี้การค้าและตั๋วเงินรับสุทธิ | 
| CurrentLiabilities | รวมหนี้สินหมุนเวียน |
| Inventory | สินค้าคงเหลือ |
| PaidUpCapital	| ทุนเรียกชำระแล้ว |
| ProperTREquipment | ที่ดิน อาคารและอุปกรณ์สุทธิ |
| ShareholderEquity | รวมส่วนของผู้เป็นหุ้นส่วน/ผู้ถือหุ้น |
| TotalAsset | รวมทรัพย์สิน |
| TotalCurrentAsset | รวมสินทรัพย์หมุนเวียน |
| TotalLiabilities | รวมหนี้สิน |
| AdminExpenses | ค่าใช้จ่ายในการขายและบริการ |
| CostOfGoodsSold | ต้นทุนขาย |
| EarningPerShare | กำไรต่อหุ้น |
| IncomeTax | ภาษีเงินได้ |
| InterestExpenses | ดอกเบี้ยจ่าย |
| NetProfit | กำไร (ขาดทุนสุทธิ) |
| SaleRevenue | รายได้หลัก |
| TotalRevenue  |	รวมรายได้ |
| StatementYear | ปี พ.ศ. ของงบการเงิน |
#### 8 [DBD-008-04] API ข้อมูลงบการเงิน (แบบข้อความในรูปแบบรูปแบบ pdf) (text-pdf)
  
(อยู่ระหว่าง DBD ปรับปรุงเป็นเวอร์ชันใหม่)

API

Response

คำอธิบายชุดข้อมูล
#### 9 [DBD-009-04] API ข้อมูลงบการเงิน (แบบรูปภาพในรูปแบบ pdf) (image-pdf)
  
API

```
https://api.egov.go.th/ws/dbd/juristic/v4/profile/financial/image/pdf?JuristicID=[JuristicID]&Year=[Year]
```

JuristicID คือ เลขทะเบียนนิติบุคคล 
Year         คือ  ปี พ.ศ. ของงบการเงินที่ต้องการเรียกข้อมูล

**Response**

```
{
  "ID": "010555917XXXX",
  "FileName": "010555917XXXX-ข้อมูลงบการเงิน (V4) (รูปภาพ)-Certificate_20201028112450.pdf",
  "FileSize": "239235",
  "Info": {
    "Name": "ข้อมูลงบการเงิน (V4) (รูปภาพ)",
    "NumberOfPage": 2
  },
  "mimeType": "application/pdf",
  "Hashes": "D6ADCBFEEDF694781C21B89135442152",
  "Result": "JVBERi0xLjcKJeLjz9MKMyAwIG9iago8PC9GVC9TaWcvVChTa..."
}
```

**คำอธิบายชุดข้อมูล**

| รายการข้อมูล | คำอธิบาย |
| -- | -- | 
| ID | เลขนิติบุคคล |
| FileName | ชื่อไฟล์ |
| FileSize | ขนาดไฟล์ (Byte) |
| INFO | |
| Name |	ชื่อเอกสาร |
| NumberOfPage | 	จำนวนหน้าทั้งหมดของเอกสาร |
| mimeType | 	ประเภทไฟล์ |
| Hashes |	แฮชไฟล์สำหรับตรวจสอบ |
| Result |  	ไฟล์ในรูปแบบ Base64 |
#### 10 [DBD-010-04] API ข้อมูลงบการเงิน (แบบรูปภาพ) (image)
  
API

```
https://api.egov.go.th/ws/dbd/juristic/v4/profile/financial/image?JuristicID=[JuristicID]&Year=[Year]
```

JuristicID คือ เลขทะเบียนนิติบุคคล
Year คือ ปี พ.ศ.

**Response**

```
{
"Type":"Financial",
"Page":10,
"Contents":[
{
"Page":0,
"Total":10,
"Type":"application/pdf",
"Size":863374,
"Data":"JVBERi0xLjQKJeLjz9MKMSAwIG9iago8PC9UeXBlL1h..."
}
]
}
```

**คำอธิบายชุดข้อมูล**

| รายการข้อมูล | คำอธิบาย |
| -- | -- |
| Type | ประเภทข้อมูล (ข้อมูลชุดนี้คือ "Objective") |
| Page | จำนวนหน้าทั้งหมด |
| Contents | | 
| Page	| หน้าของข้อมูลที่แสดง (ข้อมูลชุดนี้จะแสดงทุกหน้า Page จึงเป็น 0 เท่านั้น) |
| Total	| จำนวนหน้าทั้งหมด(หน้า) |
| Type |	ประเภทไฟล์ |
| Size |	ขนาดไฟล์(byte) |
| Data	| ไฟล์ในรูปแบบ Base64 |

#### 11 [DBD-011-04] API ข้อมูลหนังสือบริคณห์สนธิ และเอกสารประกอบ (แบบรูปภาพในรูปแบบ pdf) (image-pdf)
  
API

```
https://api.egov.go.th/ws/dbd/juristic/v4/profile/borikon/image/pdf?JuristicID=JuristicID
```

JuristicID คือ เลขทะเบียนนิติบุคคล

**Response**

```
{
  "ID": "0000000000001",
  "FileName": "0000000000001-ข้อมูลบริคณห์สนธิ (V4) รูปภาพ-Certificate_20201022134413.pdf",
  "FileSize": "183758",
  "Info": {
    "Name": "ข้อมูลบริคณห์สนธิ (V4) รูปภาพ",
    "NumberOfPage": 2
  },
  "mimeType": "application/pdf",
  "Hashes": "95F2FA460C13E56B415F2DD0373E68FB",
  "Result": "JVBERi0xLjcKJeLjz9MKMyAwIG9iago8PC9GVC9T....."
}
```

**คำอธิบายชุดข้อมูล**

| รายการข้อมูล | คำอธิบาย |
| -- | -- |
| ID | เลขนิติบุคคล |
| FileName	| ชื่อไฟล์ |
| FileSize | ขนาดไฟล์ (Byte) |
| INFO | |
| Name | ชื่อเอกสาร |
| NumberOfPage | จำนวนหน้าของเอกสาร |
| mimeType | ประเภทไฟล์ |
| Hashes | แฮชไฟล์สำหรับตรวจสอบ |
| Result | ไฟล์ในรูปแบบ Base64 |

#### 12 [DBD-012-04] API ข้อมูลหนังสือบริคณห์สนธิ และเอกสารประกอบ (แบบรูปภาพ) (image)
  
API

```
https://api.egov.go.th/ws/dbd/juristic/v4/profile/borikon/image?JuristicID=JuristicID
```

JuristicID คือ เลขทะเบียนนิติบุคคล

**Response**

```
{
  "Type": "Borikon",
  "Page": 2,
  "Contents": [
    {
      "Page": 0,
      "Total": 2,
      "Type": "application/pdf",
      "Size": 182220,
      "Data": "JVBERi0xLjQKJeLjz9MKMSAwIG9iago...."
    }
  ]
}
```

**คำอธิบายชุดข้อมูล**

| รายการข้อมูล	| คำอธิบาย |
| -- | -- |
| Type	| ชื่อไฟล์ |
| Page | จำนวนหน้าทั้งหมด |
| Content	| |
| Page | หน้าของข้อมูลที่แสดง (ข้อมูลชุดนี้จะแสดงทุกหน้า Page จึงเป็น 0 เท่านั้น) |
| Total | จำนวนหน้าทั้งหมด(หน้า) |
| Type | ประเภทไฟล์ |
| Size | ขนาดไฟล์(byte) |
| Data | ไฟล์ในรูปแบบ Base64 |

#### 13 [DBD-013-04] API ข้อมูลวัตถุประสงค์ (แบบรูปภาพ) (image)
  
**API**

```
https://api.egov.go.th/ws/dbd/juristic/v4/profile/objective/image?JuristicID=[JuristicID]
```

JuristicID คือ เลขทะเบียนนิติบุคคล
 
**Response**

```
{
"Type": "Objective",
"Page": 2,
"Contents":[
{
"Page": 0,
"Total": 2,
"Type": "application/pdf",
"Size": 46299,
"Data": "JVBERi0xLjQKJeLjz9MKMyAwIG9iago8PC9MZW5ndG..."
}
]
}
```

**คำอธิบายชุดข้อมูล**

| รายการข้อมูล	| คำอธิบาย |
| ---| --- |
| Type	| ประเภทข้อมูล (ข้อมูลชุดนี้คือ "Objective") |
| Page	| จำนวนหน้าทั้งหมด |
| Contents | |
| Page | หน้าของข้อมูลที่แสดง (ข้อมูลชุดนี้จะแสดงทุกหน้า Page จึงเป็น 0 เท่านั้น) |
| Total	| จำนวนหน้าทั้งหมด(หน้า) |
| Type | ประเภทไฟล์ |
| Size | ขนาดไฟล์(byte) |
| Data | ไฟล์ในรูปแบบ Base64 |

#### 14 [DBD-014-04] API ข้อมูลวัตถุประสงค์ (แบบรูปภาพในรูปแบบ pdf) (image-pdf)
  
API

```
http://api.egov.go.th/ws/dbd/juristic/v4/profile/objective/pdf?JuristicID=[JuristicID]
```

JuristicID คือ เลขทะเบียนนิติบุคคล
 
**Response**

```
{
"ID": "0000000000000",
"FileName": "0000000000000-ข้อมูลวัตถุประสงค์จดทะเบียนนิติบุคคล (รูปภาพ)-Certificate_20191129140702.pdf",
"FileSize": "135246",
"Info":{
"Name": "ข้อมูลวัตถุประสงค์จดทะเบียนนิติบุคคล (รูปภาพ)",
"NumberOfPage": 2,
},
"mimeType": "application/pdf",
"Hashes": "4B158C5639576E32A668653C6D7BBD88",
"Result": "JVBERi0xLjcKJeLjz9MKMyAwIG9iago8PC9GVC9TaWcvV..."
}
```

**คำอธิบายชุดข้อมูล**

| รายการข้อมูล | คำอธิบาย |
| ID | เลขทะเบียนนิติบุคคล |
| FileName | ชื่อไฟล์ |
| FileSize |	ขนาดไฟล์ (Byte) |
| mimeType | ประเภทไฟล์ |
| Hashes	| แฮชไฟล์สำหรับตรวจสอบ |
| Result	| ไฟล์ในรูปแบบ Base64 |
| Info	 | | 
| Name	| ชื่อเอกสาร |
| NumberOfPage	| จำนวนหน้าทั้งหมดของเอกสาร |

#### 15 [DBD-015-04] API ข้อมูลทะเบียนพาณิชย์ (แบบข้อความ) (text)
  
**API**

```
https://api.egov.go.th/ws/dbd/juristic/v4/profile/register?CMNO=[CMNO]
```

CMNO คือ เลขทะเบียนพานิชย์

**Response**

```
{
"ResultList":[
{
"OwnName": "นายชื่อ นามสกุล",
"Name": "ร้านนาทีทำ",
"RegisterDate": "25500129",
"ObjectDescription": "การขายส่งแผ่นซีดี แถบบันทึก วีดิทัศน์ แผ่นวีดิทัศน์ ดีวีดี หรือแผ่นวีดิทัศน์ระบบดิจิทัล",
"CMNO": "0000000000000",
"Address": "เลขที่ 0/0 ถนน.. ตำบล.. อำเภอเมืองมหาสารคาม จังหวัดมหาสารคาม รหัสไปรษณีย์00000",
"OfficeName": "เทศบาลเมือง.."
},
{
"OwnName": "นายชื่อ นามสกุล",
"Name": "นาทีทำ",
"RegisterDate": "25500129",
"ObjectDescription": "ทำการขาย-ม้วนเทป แผ่นซีดี แผ่นวีซีดี เฉพาะเกี่ยวกับการบันเทิงเท่านั้น",
"CMNO": "0000000000000",
"Address": "เลขที่ 0/0 ถนน.. ตำบล.. อำเภอเมือง.. จังหวัด.. รหัสไปรษณีย์00000",
"OfficeName": "เทศบาลเมือง.."
}
],
"RawData": "PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz...."
}
```

**คำอธิบายชุดข้อมูล**

| รายการข้อมูล | คำอธิบาย |
| -- | -- |
| OwnName | ชื่อ นามสกุล เจ้าของ |
| Name | ชื่อนิติบุคคล |
| RegisterDate | ปี พ.ศ. เดือน วัน ที่ลงทะเบียน "YYYYMMDD" |
| ObjectDescription | รายละเอียดวัตถุประสงค์ |
| CMNO | เลขทะเบียนพานิชย์ |
| Address | ที่อยู่ |
| OfficeName | ชื่อหน่วยงานที่จดทะเบียนพานิชย์ |
| RawData	| ข้อมูลต้นฉบับ Base64 |

#### 16 [DBD-016-04] API ข้อมูลทะเบียนพาณิชย์ (แบบข้อความในรูปแบบ pdf) (text-pdf)
  
**API**

```
https://api.egov.go.th/ws/dbd/juristic/v4/profile/register/pdf?CMNO=[CMNO]
```

CMNO คือ เลขทะเบียนพานิชย์

**Response**

```
{
"ID": "0000000000000",
"FileName": "0000000000000-ข้อมูลทะเบียนพานิชย์ (V4)-Certificate_20200103151957.pdf",
"FileSize": "160260",
"mimeType": "application/pdf",
"Hashes": "7BA9697C96387FD31EE9D96E61166764",
"Result": "JVBERi0xLjcKJeLjz9MKMyAwIG9iago8PC9GVC...."
}
```

**คำอธิบายชุดข้อมูล**

| รายการข้อมูล | คำอธิบาย |
| -- | -- |
| ID	| เลขทะเบียนนิติบุคคล |
| FileName | ชื่อไฟล์ |
| FileSize	| ขนาดไฟล์ (Byte) |
| mimeType |	ประเภทไฟล์ |
| Hashes |	แฮชไฟล์สำหรับตรวจสอบ |
| Result |	ไฟล์ในรูปแบบ Base64 |

#### 17 [DBD-017-04] API หนังสือรับรองและข้อมูลทะเบียนการประกอบธุรกิจของคนต่างด้าว (แบบข้อความ) (text)
  
**API**

```
https://api.egov.go.th/ws/dbd/juristic/v4/profile/foreigner?ID=[ID]
```

ID คือ เลขทะเบียนนิติบุคคล

**Response**

```
{
"ResultList":[
{
"Name": "หนังสือรับรองตาม ปว. 281",
"PermitDate": "1974-07-09 00:00:00.0",
"MinCap": "0",
"LicenseNo": "1/2529",
"AppID13": "0000000000000",
"NameTH": "บริษัท ตัวอย่าง (ไทย) จำกัด",
"NameEN": "EXAMPLE (THAILAND) LIMITED",
"CountryShort": "ไทย",
"Status": "ดำเนินกิจการ",
"StartDate": "1972-11-26 00:00:00.0",
"EndDate": null,
"Address": "00 อาคาร.. ชั้นที่ 00 และ 00 ถนนสีลม ",
"Tumbon": "สีลม",
"Ampur": "เขตบางรัก",
"Province": "กรุงเทพมหานคร",
"CMName": "นายชื่อ1 นามสกุล1 นายชื่อ2 นามสกุล2 นายชื่อ3 นามสกุล3",
"DRTextName": null,
"BizDetail1": "บัญชี ค. หมวด 1(1) การค้าส่งสินค้าทุกชนิดในประเทศ นอกจากการค้าผลิตผลทางเกษตรพื้น เมือง ตามที่ระบุไว้ในบัญชี ก.",
"BizDetail2": null,
"BizDetail3": null,
"BizDetail4": null
}
],
"RawData": "PD94bWwgdmVyc2lvbj0iMS4wIi...";
}
```

**คำอธิบายชุดข้อมูล**

| รายการข้อมูล |	คำอธิบาย |
| -- | -- |
| Name | ชื่อใบอนุญาต |
| PermitDate | วันที่อนุญาต |
| MinCap | ทุนจดทะเบียนขั้นต่ำ |
| LicenseNo | เลขที่ใบอนุญาต |
| AppID13 | เลขทะเบียน 13 หลัก |
| NameTH | ชื่อผู้ขออนุญาต (ไทย) |
| NameEN | ชื่อผู้ขออนุญาต (อังกฤษ) |
| CountryShort | ประเทศของผู้ถือหุ้นหลัก |
| Status | สถานะใบอนุญาต |
| StartDate | วันที่เริ่ม |
| EndDate | วันที่หมดอายุ |
| Address | ที่ตั้งสำนักงาน |
| Tumbon | ตำบล |
| Ampur | อำเภอ |
| Province | จังหวัด |
| CMName | ชื่อกรรมการ |
| DRTextName | ผู้รับผิดชอบผูกผัน |
| BizDetail1 | ธุรกิจที่ได้รับอนุญาต1 |
| BizDetail2 | ธุรกิจที่ได้รับอนุญาต2 |
| BizDetail3 | ธุรกิจที่ได้รับอนุญาต3 | 
| BizDetail4 | ธุรกิจที่ได้รับอนุญาต4 |
| RawData	| ข้อมูลต้นฉบับ Base64 |

#### 18 [DBD-018-04] API หนังสือรับรองและข้อมูลทะเบียนการประกอบธุรกิจของคนต่างด้าว (แบบข้อความในรูปแบบ pdf) (text-pdf)
  
API

https://api.egov.go.th/ws/dbd/juristic/v4/profile/foreigner/pdf?ID=[ID]
ID คือ เลขทะเบียนนิติบุคคล
Response

BODY
{
"ID": "0000000000000",
"FileName": "0000000000000-ข้อมูลการประกอบธุรกิจของคนต่างด้าว-Certificate_20200108125235.pdf",
"FileSize": "184930",
"mimeType": "application/pdf",
"Hashes": "C71E2966295698A50F38382E96117B0F",
"Result": "JVBERi0xLjcKJeLjz9MKMyAwIG9iago8PC9...";
}
JSON
คำอธิบายชุดข้อมูล

 

รายการข้อมูล	คำอธิบาย
ID	เลขนิติบุคคล
FileName	ชื่อไฟล์
FileSize	ขนาดไฟล์ (Byte)
mimeType	ประเภทไฟล์
Hashes	แฮชไฟล์สำหรับตรวจสอบ
Result	ไฟล์ในรูปแบบ Base64

#### 19 [DBD-019-04] API ข้อมูลเบื้องต้นหลักสัญญาประกันธุรกิจ (แบบข้อความ) (text)
  
API

https://api.egov.go.th/ws/dbd/juristic/v4/profile/guarantee?EsecureNo=[EsecureNo]
EsecureNo คือ เลขสัญญาหลักประกันทางธุรกิจ
Response

BODY
{
"ResultList":[
{
"ESecureNo": "2559070000874",
"Creditors": "ธนาคารธนชาต",
"RegisterDatetime": "2016-07-04 08:30:00.0",
"RequestNo": "5906010035804"
}
],
"RawData": "PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0i"
}
JSON
คำอธิบายชุดข้อมูล

รายการข้อมูล	คำอธิบาย
ESecureNo	เลขสัญญาหลักประกันทางธุรกิจ
Creditors	ชื่อผู้รับหลักประกัน
RegisterDatetime	วัน เวลาที่จดทะเบียนสัญญาหลักประกันทางธุรกิจ
RequestNo	เลขที่คำขอ
RawData	ข้อมูลต้นฉบับ Base64

#### 20 [DBD-020-04] API ข้อมูลเบื้องต้นหลักสัญญาประกันธุรกิจ (แบบข้อความในรูปแบบ pdf) (text-pdf)
  
API

https://api.egov.go.th/ws/dbd/juristic/v4/profile/guarantee/pdf?EsecureNo=[EsecureNo]
EsecureNo คือ เลขสัญญาหลักประกันทางธุรกิจ
Response

BODY
{
"ID": "0000000000000",
"FileName": "0000000000000-ข้อมูลทะเบียนสัญญาหลักประกันธุรกิจ (V4)-Certificate_20200110172500.pdf",
"FileSize": "156024",
"mimeType": "application/pdf",
"Hashes": "E2CE93F3419505F1371F223509600D72",
"Result": "JVBERi0xLjcKJeLjz9MKMyAwIG9iago8PC9..."
}
JSON
คำอธิบายชุดข้อมูล

รายการข้อมูล	คำอธิบาย
ID	เลขนิติบุคคล
FileName	ชื่อไฟล์
FileSize	ขนาดไฟล์ (Byte)
mimeType	ประเภทไฟล์
Hashes	แฮชไฟล์สำหรับตรวจสอบ
Result	ไฟล์ในรูปแบบ Base64 

#### 21 [DBD-021-04] API ค้นหาข้อมูลทะเบียนนิติบุคคล ด้วยชื่อนิติบุคคล (แบบข้อความ) (text)
  
API

https://api.egov.go.th/ws/dbd/juristic/v4/profile/infobyname?Name=[JuristicName]
Name คือ ชื่อนิติบุคคล ภาษาไทย เช่น Name=วิทยเทคโนโลยี
 

Response

BODY
{
"ResultList":[
{
"JuristicType": "3",
"JuristicTypeName": "ห้างหุ้นส่วนจำกัด",
"JuristicID": "0000000000000",
"JuristicName": "วิทยเทคโนโลยี ตัวอย่าง",
"JuristicStatus": "ยังดำเนินกิจการอยู่",
"RegisterDate": "25530318",
"NFName": "วิทยเทคโนโลยีตัวอย่าง"
}
],
"RawData": "PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZG..."
}
JSON
 

คำอธิบายชุดข้อมูล

รายการข้อมูล	คำอธิบาย
JuristicType	หมายเลขประเภทนิติบุคคล
JuristicTypeName	ชื่อประเภทนิติบุคคล
JuristicID	เลขทะเบียนนิติบุคคล
JuristicName	ชื่อนิติบุคคล
JuristicStatus	สถานะนิติบุคคล
RegisterDate	วันที่จดทะเบียน ปี พ.ศ. เดือน วัน เช่น "25621021"
NFName	ชื่อนิติบุคคล
RawData	ข้อมูลต้นฉบับ Base64

#### 22 [DBD-022-04] API ค้นหาข้อมูลทะเบียนนิติบุคคล ด้วยชื่อและนามสกุลกรรมการ (แบบข้อความ) (text)
  
API

https://api.egov.go.th/ws/dbd/juristic/v4/profile/infobycommittee?Name=[CommitteName(Space)CommitteSurname]
Name คือ ชื่อกรรมการ(เว้นวรรค)นามสกุลกรรมการ เช่น Name=ใจดี ทำดี
 

Response

BODY
{
"ResultList":[
{
"CommitteeName": "ใจดี ทำดี",
"CommitteeDetail":[
{
"CommitteeName": "ใจดี ทำดี",
"JuristicID": "0000000000001",
"JuristicName": "หจ.ตัวอย่างมัลติคัลเลอร์",
"JuiristicStatus": "เสร็จการชำระบัญชี"
},
{
"CommitteeName": "ใจดี ทำดี",
"JuristicID": "0000000000002",
"JuristicName": "หจ.ตัวอย่าง คอมพิวเตอร์ เซอร์วิส",
"JuiristicStatus": "เสร็จการชำระบัญชี"
},
{
"CommitteeName": "ใจดี ทำดี",
"JuristicID": "0000000000003",
"JuristicName": "บจ.ตัวอย่าง จำกัด",
"JuiristicStatus": "ยังดำเนินกิจการอยู่"
}
]
}
],
"RawData": "PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVV..."
}
JSON
 

คำอธิบายชุดข้อมูล

รายการข้อมูล	คำอธิบาย
CommitteeName	ชื่อ นามสกุล กรรมการ
CommitteeDetail	 
CommitteeName	ชื่อ นามสกุล กรรมการ
JuristicID	เลขทะเบียนนิติบุคคล
JuristicName	ชื่อนิติบุคคล
JuristicStatus	สถานะนิติบุคคล
RawData	ข้อมูลต้นฉบับ Base64
