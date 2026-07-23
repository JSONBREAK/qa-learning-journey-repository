> API คืออะไร, Client-Server, ทำไม QA ต้องเทส API

---
# API Concepts for QA

เอกสารปูพื้นฐานแนวคิดเกี่ยวกับ **API (Application Programming Interface)** สำหรับ Quality Assurance (QA) เพื่อเข้าใจบทบาท ปัญหาที่ต้องตรวจจับ และโครงสร้างสถาปัตยกรรมพื้นฐานในการทดสอบซอฟต์แวร์

---
## 📌 1. API คืออะไร? (ในมุมมองของ QA)

**API (Application Programming Interface)** คือ "ตัวกลาง" หรือเปรียบเสมือน "พนักงานเสิร์ฟ" ที่รับคำสั่งจากฝั่งผู้ใช้ (Client/Frontend) นำไปบอกระบบหลังบ้าน (Server/Backend) แล้วนำผลลัพธ์กลับมาส่งคืน

### 💡 ทำไม QA ต้องทดสอบ API ไม่รอเทสแค่บน UI?

1. **Shift-Left Testing (เจอปัญหาเร็วขึ้น):** การทดสอบ API ทำได้ตั้งแต่ฝั่ง Backend พัฒนาเสร็จ โดยไม่ต้องรอ UI ทำเสร็จ ยิ่งพบ Bug เร็ว ค่าใช้จ่ายในการแก้ยิ่งต่ำ
2. **Business Logic Validation:** กฎธุรกิจ (Business Logic) ส่วนใหญ่อยู่ที่หลังบ้าน การเทสผ่าน API ช่วยยืนยันว่าเงื่อนไขระบบทำงานถูกต้องจริง ไม่ถูกหลอกด้วยการ Bypass หน้า UI
3. **Security Check:** ป้องกันผู้ไม่หวังดีแอบยิง API เข้ามาตรงๆ โดยไม่ผ่านหน้าเว็บ/แอป หาก Backend ไม่มีการตรวจสอบข้อมูล ป้องกันเพียงแค่ UI ระบบจะเกิดช่องโหว่ร้ายแรง
4. **Faster Execution:** การยิง API ใช้เวลาสั้นกว่าการรัน Test ผ่าน UI แบบ Automation มาก ช่วยให้ feedback loop เร็วขึ้น

---
## 🏛️ 2. Client-Server Architecture & QA Mindset

การทำงานส่วนใหญ่ของ Web และ Mobile Application ใช้รูปแบบ **Client-Server Architecture**

```text
+-------------------+                   +-------------------+
|                   |  --- Request ---> |                   |
|  Client (Front)   |                   |  Server (Back)    |
| (Web/Mobile App)  | <--- Response --- | (Database/Logic)  |
+-------------------+                   +-------------------+
```

```
🔹Request ประกอบด้วย
	- URL 
	- HTTP Method
	- Headers 
	- Body (Optional)
  
🔹Response ประกอบด้วย
	- HTTP Status Code 
	- Headers 
	- Body
```
#### 🔍 วิธีการแยกแยะ Bug เมื่อเกิดปัญหา (Frontend vs Backend)

>เวลาเกิด Bug ขึ้นในระบบ QA ต้องแยกแยะให้ได้ว่าปัญหานั้นมาจากฝั่งไหน 
> โดยดูจาก Request/Response Payload:

| **อาการของ Bug**                                           | **จุดที่น่าจะพัง**     | **แนวทางการวิเคราะห์**                                                                     |
| ---------------------------------------------------------- | ---------------------- | ------------------------------------------------------------------------------------------ |
| กดปุ่มแล้วไม่มีอะไรเกิดขึ้น / UI ค้าง                      | **Frontend**           | เปิด Network Tab ดู พบว่าปุ่มไม่มีการ trigger ส่ง Request ออกไป                            |
| กรอกฟอร์มถูก แต่นำส่งไม่ได้                                | **Frontend / Request** | เช็ก Payload ที่ส่งไป พบว่า Frontend Format ข้อมูลผิด หรือส่ง Key ไม่ตรงกับที่ API ต้องการ |
| ส่ง Request ถูกตาม Spec แต่ได้ `500 Internal Server Error` | **Backend**            | API หลังบ้านประมวลผลผิดพลาด Crash หรือ Handling Exception ไม่ครอบคลุม                      |
| ส่ง Request ถูก แต่ Response ได้ข้อมูลไม่ตรงกับ Database   | **Backend / Database** | Logic การ Query ข้อมูลหรือการคำนวณหลังบ้านผิด                                              |
| Response ขาด Field ที่ Spec กำหนด                          | Backend                | ตรวจสอบ Response เทียบกับ API Specification                                                |
| Status Code ไม่ตรงที่คาดหวัง                               | Backend                | เช่น ควรได้ `404` แต่กลับได้ `200`                                                         |

---

## 📄 3. รูปแบบการรับส่งข้อมูลยอดนิยม: JSON

ในการทดสอบ API ยุคปัจจุบัน รูปแบบข้อมูลที่นิยมใช้ส่งไป-กลับมากที่สุดคือ **JSON (JavaScript Object Notation)**

ตัวอย่างโครงสร้าง JSON :

```
{
  "orderId": "ORD-12345",
  "totalAmount": 500.00,
  "isPaid": true,
  "items": [
    {
      "productId": "P001",
      "quantity": 2
    }
  ],
  "customer": null
}
```

### 🎯 จุดสังเกต Data Types ใน JSON สำหรับ QA:

- **String:** ข้อความ อยู่ในเครื่องหมาย `" "` (เช่น `"ORD-12345"`)
- **Number:** ตัวเลข ไม่มีเครื่องหมายคำพูด (เช่น `500.00`)
- **Boolean:** ค่าความจริง มีแค่ `true` หรือ `false`
- **Array:** รายการข้อมูล อยู่ในเครื่องหมาย `[ ]` (เช่น รายการสินค้า `items`)
- **Object:** กลุ่มของข้อมูล อยู่ในเครื่องหมาย `{ }`
- **Null:** ค่าว่าง `null` (ต้องเช็กว่า API ควรส่งค่าว่างมาได้หรือไม่)

---

## 📝 Summary

ในบทนี้ได้เรียนรู้ว่า

- API คือช่องทางการสื่อสารระหว่าง Client และ Server
- QA ควรทดสอบ API เพื่อค้นหา Bug ได้เร็วและตรวจสอบ Business Logic
- การสื่อสารผ่าน API อยู่ในรูปแบบ Request และ Response
- JSON เป็นรูปแบบข้อมูลที่นิยมใช้มากที่สุดในการแลกเปลี่ยนข้อมูล
- QA ควรสามารถวิเคราะห์เบื้องต้นได้ว่าปัญหาเกิดจาก Frontend หรือ Backend

ในบทถัดไป เราจะเรียนรู้พื้นฐานของ HTTP ซึ่งเป็นโปรโตคอลที่ API ส่วนใหญ่ใช้ในการสื่อสาร