+++
title = "ข้อมูลบุคคล Linkage Center กรมการปกครอง"
weight = 17
+++

### การเรียกข้อมูลบุคคลจากฐานข้อมูล Linkage (5000)
  
ทำการเรียกขอข้อมูล จาก API Linkage ต้องทําการเรียกผ่าน Url และ Parameter ดังนี้

| รายการข้อมูล | รายละเอียด |
| --- | --- |
| วิธีการ | GET |
| URL | https://api.egov.go.th/ws/dopa/linkage/v1/link?OfficeID=<OfficeID>&ServiceID=<ServiceID>&Version=<Version>&CitizenID=<CitizenID> |
 
| Parameter | Required | Type | Description |
| --- | --- | -- | -- |
| OfficeID | Required | String | หมายเลขหน่วยงานผู้ให้บริการข้อมูล |
| ServiceID | Required | String | หมายเลขชุดข้อมูล |
| Version | Required | String | เวอร์ชันชุดข้อมูล |
| CitizenID | Required | String | หมายเลขบัตรประจําตัวประชาชน 13 หลัก ของบุคคลที่ต้องการทราบข้อมูล |

OfficeID, ServiceID และ Version สามารถดูได้จากhttps://linkagemgmt.bora.dopa.go.th/#/

#### การเรียกข้อมูลบุคคลจากฐานข้อมูล Linkage (6000)

| รายการข้อมูล | รายละเอียด |
| --- | --- |
| วิธีการ | POST |
| URL | https://api.egov.go.th/ws/dopa/linkage/v1/link?OfficeID=<OfficeID>&ServiceID=<ServiceID>&Version=<Version> | 

| Parameter | Required | Type | Description |
| --- | --- | -- | -- |
| OfficeID | Required | String | หมายเลขหน่วยงานผู้ให้บริการข้อมูล |
| ServiceID | Required | String | หมายเลขชุดข้อมูล |
| Version | Required | String | เวอร์ชันชุดข้อมูล |

OfficeID, ServiceID และ Version สามารถดูได้จาก https://linkagemgmt.bora.dopa.go.th/#/

![ตัวอย่างวิธีการเรียกข้อมูล](/images/gdx/api-linkage.png)

ข้อมูลที่ระบุใน Body สามารถดูเพิ่มเติมได้ที่ Key ตามที่ระบุใน Service สามารถดูได้จากhttps://linkagemgmt.bora.dopa.go.th/#/

### การตรวจสอบสถานะ
  
| รายการข้อมูล | รายละเอียด |
| --- | --- |
| วิธีการ | GET |
| URL | https://api.egov.go.th/ws/dopa/linkage/v1/agent/permission?Consumer=ConsumerKey&CitizenID=AgentID |

| Parameter | Required | Type | Description |
| -- | -- | -- | -- |
| Consumer | Required | String | Consumer Key  ที่ทาง สพร. จัดส่งให้ |
| Citizen ID | Required | String | หมายเลขบัตรประจําตัวประชาชน 13 หลัก ของบัตรที่ต้องการตรวจสอบถานะในการ Login AMI สพร. |

Response  มี 3 state ดังนี้

1. AgentNotAvailable

```
{
"AgentID": "0000000000000",
"CitizenID": "0000000000000",
"SessionState": "AgentNotAvailable"
}
```
​
2. AgentAvailable

```
{
"AgentID": "1102200103392",
"CitizenID": "0000000000000",
"SessionState": "AgentAvailable"
}
```
​

3. CitizenAvailable

```
{
"AgentID": "1102200103392",
"CitizenID": "1102200103392",
"SessionState": "CitizenAvailable"
}
```
​