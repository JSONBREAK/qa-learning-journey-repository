> HTTP Request/Response Structure, Methods, Status Codes, Headers

# HTTP Basics for QA

พื้นฐานของ **HTTP (Hypertext Transfer Protocol)** ซึ่งเป็นโปรโตคอลที่ใช้สื่อสารระหว่าง Client และ Server และเป็นพื้นฐานสำคัญสำหรับการทดสอบ API

--- 
## 🌐 1. HTTP คืออะไร? 

**HTTP (Hypertext Transfer Protocol)** คือ โปรโตคอลสำหรับรับส่งข้อมูลระหว่าง Client และ Server

* **HTTPS (Secure):** คือ HTTP ที่มีการเข้ารหัสข้อมูลผ่าน **TLS (Transport Layer Security)** เพื่อป้องกันการดักจับหรือแก้ไขข้อมูลระหว่างการสื่อสาร

---
## 🧱 2. โครงสร้างของ HTTP Request & Response

```text 
+-----------+                       +-----------+ 
|  Client   | ---- HTTP Request --> |  Server   | 
| (Browser) | <--- HTTP Response ---|           |                               
+-----------+                       +-----------+ 
```

### 📤 องค์ประกอบของ HTTP Request
1. **URL / Endpoint:** ที่อยู่ของ API เช่น `https://api.example.com/v1/users`
2. **HTTP Method:** คำสั่งบอกจุดประสงค์ของการเรียกใช้งาน (เช่น `GET`, `POST`)
3. **Headers:** ข้อมูลอธิบายเพิ่มเติมเกี่ยวกับ Request เช่น
	* `Content-Type: application/json` (บอก Server ว่าข้อมูลที่เราส่งไปอยู่ในรูปแบบ JSON)
	* `Authorization: Bearer <token>` (ส่ง Token ยืนยันตัวตน)
	* `Accept: application/json` (ระบุชนิดของข้อมูลที่ Client ต้องการรับกลับมาจาก Server)
4. **Body:** ข้อมูลที่ส่งไปยัง Server (ใช้กับ POST, PUT, PATCH เป็นหลัก)
### 📥 องค์ประกอบของ HTTP Response 
1. **HTTP Status Code:** รหัสตัวเลขบอกสถานะการประมวลผล (เช่น `200`, `401`, `500`) 
2. **Headers:** ข้อมูลเสริมจาก Server ตอบกลับมา เช่น `Content-Type`, `Cache-Control` 
3. **Body:** ข้อมูลที่ Server ตอบกลับมาให้ Client นำไปใช้งานต่อ (มักอยู่ในรูปแบบ JSON)

---
## 🛠️ 3. HTTP Methods ยอดนิยม 

HTTP Method บอกให้ Server รู้ว่าเราต้องการทำอะไรกับข้อมูลชุดนั้น: 

| Method       | การนำไปใช้งาน                              | มี Request Body ไหม? |         Idempotent?*         |
| :----------- | :----------------------------------------- | :------------------: | :--------------------------: |
| **`GET`**    | **อ่าน/ดึงข้อมูล** (Read)                  |        ไม่มี         |             ใช่              |
| **`POST`**   | **สร้างข้อมูลใหม่** (Create)               |          มี          |            ไม่ใช่            |
| **`PUT`**    | **อัปเดตข้อมูลทั้งหมด** (Replace/Update)   |          มี          |             ใช่              |
| **`PATCH`**  | **อัปเดตข้อมูลเฉพาะส่วน** (Partial Update) |          มี          | **ขึ้นอยู่กับการออกแบบ API** |
| **`DELETE`** | **ลบข้อมูล** (Delete)                      |        อาจมี         |             ใช่              |
> **📝 Note:** โดยทั่วไป `DELETE` มักไม่มี Request Body แต่บาง Framework หรือ API อาจรองรับการส่ง Request Body ได้


> **💡 QA Insight — Idempotent คืออะไร?** 
> **Idempotent** หมายถึง การส่ง Request เดิมซ้ำหลายครั้งแล้วผลลัพธ์สุดท้ายของระบบบน Database ยังคงเหมือนเดิม
> - **GET** - ยิงซ้ำกี่ครั้งก็ไม่เปลี่ยนข้อมูล
> - **PUT** - ส่งข้อมูลเดิมซ้ำ ผลลัพธ์สุดท้ายยังเหมือนเดิม
> - **DELETE** - ลบสำเร็จแล้ว ยิงซ้ำก็ไม่ทำให้เกิดข้อมูลเพิ่ม
> - **POST** - ยิงซ้ำมักสร้างข้อมูลใหม่ จึงไม่เป็น Idempotent
> - **PATCH** - อาจเป็นหรือไม่เป็น Idempotent ขึ้นอยู่กับการออกแบบ API (เช่น ถ้าส่งเพื่อบวกค่าเพิ่ม `count = count + 1` จะไม่เป็น Idempotent)

---

## 🚦 4. HTTP Status Codes Cheat Sheet 
เวลาทดสอบ API สิ่งแรกที่ QA ต้องกวาดตากลับมามองคือ **Status Code** ซึ่งแบ่งออกเป็น 5 กลุ่มหลัก: 

```text 
1xx : Informational (ข้อมูลแจ้งเพื่อทราบ) 
2xx : Success (ทำงานสำเร็จ) 
3xx : Redirection (ส่งต่อไปยัง URL อื่น) 
4xx : Client Error (ฝั่งผู้ใช้ส่งข้อมูลผิด) 
5xx : Server Error (ฝั่งหลังบ้านมีปัญหา)
```

### 🎯 Status Codes ที่พบบ่อยที่สุดใน Test Cases:

#### 🟢 2xx — Success (เคส Positive)
- `200 OK`: ดึงข้อมูล, อัปเดต หรือลบสำเร็จ
- `201 Created`: สร้าง Data ใหม่สำเร็จ (มักได้จากการยิง `POST`)
- `204 No Content`: ทำงานสำเร็จ แต่ไม่มี Body ตอบกลับมา (มักใช้กับ `DELETE`)
    

#### 🟡 4xx — Client Error (เคส Negative / Security)
- `400 Bad Request`: พารามิเตอร์ผิด, ลืมส่ง Required Field หรือ JSON Format พัง
- `401 Unauthorized`: ไม่ได้ใส่ Token, Token หมดอายุ หรือยิงเข้ามาโดยไม่ได้ Login
- `403 Forbidden`: มี Token แล้ว แต่ **ไม่มีสิทธิ์** เข้าถึงข้อมูลนี้ (เช่น User ปกติพยายามแอบยิง API ของ Admin)
- `404 Not Found`: ไม่พบ URL นี้ หรือหาข้อมูล ID ที่ระบุไม่เจอ
- `405 Method Not Allowed`: ใช้ HTTP Method ไม่ถูกต้อง เช่น ส่ง `POST` ไปยัง Endpoint ที่รองรับเฉพาะ `GET`
- `415 Unsupported Media Type`: ส่ง `Content-Type` ไม่ถูกต้อง เช่น API รองรับเฉพาะ `application/json`
- `422 Unprocessable Entity`: ส่ง Format ถูกแต่ข้อมูลผิดเงื่อนไข Business Logic (เช่น ส่งอายุ = -5)
    

#### 🔴 5xx — Server Error (เคส System Bug)
- `500 Internal Server Error`: Code หลังบ้าน Crash, Handling Exception ไม่ดี หรือ Database Connection หลุด
- `502 Bad Gateway`: Server ตัวหน้า (เช่น Nginx) ติดต่อ App Server หลังบ้านไม่ได้
- `503 Service Unavailable`: Server ล่ม หรือปิดปรับปรุงระบบ

---
## 📝 Summary

- HTTP เป็นโปรโตคอลการสื่อสารหลักระหว่าง Client และ Server
- Request และ Response มีองค์ประกอบสำคัญอย่าง Headers, Body และ Status Code
- HTTP Methods ต่างๆ มีวัตถุประสงค์และการจัดการข้อมูลบน Database ที่แตกต่างกัน (Idempotent vs Non-Idempotent)
- Status Codes ช่วยให้ QA ระบุได้ทันทีว่าเคสทดสอบนั้น Success (`2xx`), มีข้อผิดพลาดฝั่ง Input (`4xx`), หรือระบบหลังบ้านพัง (`5xx`)

---

## ➡️ Next Chapter

ในบทถัดไป เราจะเริ่มใช้งาน **Postman** เพื่อส่ง HTTP Request จริง วิเคราะห์ Response และเรียนรู้วิธีทดสอบ API เบื้องต้น