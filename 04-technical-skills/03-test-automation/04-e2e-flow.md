# 04 – E2E Flow: Business Scenario Layer

## 🎯 Purpose
E2E Flow คือการทดสอบระบบจากมุมมองของผู้ใช้จริง โฟกัสที่ Business behavior ไม่ใช่ implementation detail

ไฟล์นี้เน้น:
- Scenario design
- Test granularity
- State management
- Data lifecycle

ไม่ลงรายละเอียด:
- Locator strategy
- Page Object implementation
- Technical selector detail

---

## 🧱 1️⃣ Business Scenario Thinking
E2E Test ต้องตอบคำถาม:
- ผู้ใช้ทำอะไร?
- ระบบต้องตอบสนองอย่างไร?

ตัวอย่าง Business Scenario:
- User สมัครสมาชิก → login → สั่งซื้อสินค้า → เห็น order ใน history
- Admin สร้างโปรโมชั่น → User ใช้โปรโมชั่นได้จริง

E2E ไม่ใช่:
- ทดสอบปุ่มทุกปุ่ม
- ตรวจ element ทุก field
- ไล่ click ทั้งหน้าเว็บ

E2E คือการ validate ว่า business flow ทำงานได้ครบ

---

## ✅ 2️⃣ Happy Path vs Negative Path
**Happy Path**
- Flow ปกติที่ผู้ใช้ทำสำเร็จ เช่น สมัครสมาชิก, ชำระเงิน, สร้าง order
- Happy path ต้องมีอย่างน้อย 1 เส้นต่อ feature สำคัญ

**Negative Path**
- ทดสอบ behavior เมื่อเกิดความผิดพลาด เช่น ชำระเงินด้วยบัตรหมดอายุ, กรอก OTP ผิด
- เน้น business-impact error ไม่จำเป็นต้อง negative ครบทุก field

---

## 🔄 3️⃣ State Dependency Awareness
- Test ควร independent
- หลีกเลี่ยง shared mutable state
- อย่าให้ลำดับการรันมีผลกับผลลัพธ์
- E2E ที่ดี: รันเดี่ยวได้, รัน parallel ได้, รันซ้ำได้

---

## 🗂 4️⃣ Data Setup & Cleanup Strategy
- ไม่ควรพึ่งพาข้อมูลในระบบที่ควบคุมไม่ได้
- Seed data ผ่าน API, create user via backend shortcut, ใช้ dedicated test account
- Cleanup data หลัง test เพื่อ deterministic test

---

## 🚫 5️⃣ Avoid Chaining Unrelated Features
- 1 E2E flow = 1 business objective
- ถ้า feature ไม่เกี่ยวกัน อย่าผูกใน test เดียว
- หลีกเลี่ยง mega flow ที่ debug ยาก, maintenance cost สูง

---

## 🎯 6️⃣ Test Granularity
**Layer | Scope**
- Unit: Function logic
- Integration: Service interaction
- E2E: Critical business flow

E2E ควร validate core revenue flow, security-sensitive flow, high-risk scenario

---

## 🧠 Designing Maintainable E2E Suite
- Feature นี้ critical ไหม?
- ถ้ามันพัง ลูกค้าจะเดือดร้อนแค่ไหน?
- เราต้องการ coverage หรือ confidence?
- E2E ไม่ใช่เรื่อง coverage สูง แต่คือเรื่อง confidence สูง

---

## 📌 Final Principles
- E2E = Business confidence, not UI coverage
- 1 flow = 1 business goal
- Happy path สำคัญที่สุด
- Negative path ต้องเน้น business impact
- Test ต้อง independent
- Data ต้องควบคุมได้
- อย่าเขียน mega scenario

---


## 🚫 When NOT to Write E2E
ไม่ควรเขียน E2E หาก:
- เป็น validation logic เล็ก ๆ (ควรอยู่ integration/unit)
- เป็น UI cosmetic change
- เป็น edge case ที่ไม่มี business impact
- สามารถ validate ได้เร็วกว่าใน lower layer

---

## 🏗 E2E Pyramid Awareness
E2E อยู่บนสุดของ Test Pyramid
จำนวนควรน้อยกว่า integration และ unit
ถ้า E2E เยอะเกินไป แปลว่า test strategy อาจผิด layer

---

## 💸 Cost Awareness
E2E ช้า
รันบน CI แพง
Debug time สูง
Maintenance cost สูงกว่า lower layer
ทุก E2E test มี maintenance cost จึงต้องมี business justification

---

## 🧠 Senior Mindset
- E2E suite ควรเล็ก แต่ทรงพลัง
- Flaky E2E ทำลายความเชื่อมั่นทีม
- Automation ต้องเพิ่มความมั่นใจ ไม่ใช่เพิ่มภาระ
- ทุก E2E test ควรมีเหตุผลทางธุรกิจรองรับ
- Stable E2E = Reliable Release = Business Confidence
