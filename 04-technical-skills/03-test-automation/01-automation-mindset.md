# Automation Mindset


## 1️⃣ What is Test Automation (นิยาม)
Test Automation คือการใช้ซอฟต์แวร์เพื่อ validate system behavior อย่าง repeatable, reliable และ scalable ไม่ใช่แค่การเอา manual test มาเขียนเป็น script

**เป้าหมายของ Automation:**
- ลด regression effort
- เพิ่ม confidence ก่อน release
- เพิ่ม feedback speed
- ลด human error

**Business Impact:**
Automation exists to support faster and safer releases.
It should reduce business risk, not just validate features.

---

## 2️⃣ When NOT to Automate (สำคัญมาก)
ไม่ควร automate ทุกอย่าง เช่น:
- UI ที่ยัง unstable
- One-time test
- Exploratory test
- Highly visual test
- Requirement ที่เปลี่ยนบ่อยมาก

นี่คือ mindset ที่แสดงว่าคุณคิดเรื่อง ROI

---


## 3️⃣ ROI & Cost of Automation
Automation มี cost:
- Development time
- Maintenance cost
- Flaky test impact
- Infrastructure cost

ควร automate กับ High-risk + High-repeat + Stable feature เท่านั้น

**Business Impact:**
Automation should help the business release with confidence and reduce risk, not just validate features.

---


## 4️⃣ Deterministic & Predictable Tests
Test ที่ดีต้อง:
- รัน 100 ครั้งได้ผลเหมือนเดิม
- ไม่ขึ้นกับลำดับ test
- ใช้ controlled test data
- reproducible
- ไม่พึ่ง external unstable systems

นี่คือหัวใจของ automation engineer

---

## 5️⃣ Test Isolation
Test ต้องไม่ share state, ไม่พึ่ง test ก่อนหน้า, ไม่ใช้ global variable, ไม่พึ่ง data จริงจาก production

Isolation ช่วยลด flaky test

---


## 6️⃣ Flaky Test คือศัตรู
Flaky test คือ test ที่ผลลัพธ์ไม่แน่นอน

**สาเหตุ:** timing, async, shared state, unstable locator
**ผลกระทบ:** ทำให้ทีมเสียเวลา, ขาดความมั่นใจ
Flaky tests reduce trust in the automation suite. Once trust is lost, failures are ignored.
**วิธีลด:** isolate test, หลีกเลี่ยง sleep, ใช้ locator ที่เสถียร

บริษัทชอบ QA ที่เข้าใจปัญหานี้

---

## 7️⃣ Automation Pyramid
```
Unit (เยอะสุด)
Integration
API
E2E (น้อยสุด)
```
E2E test แพงและช้า ไม่ควรมีเยอะเกินไป

---

## 8️⃣ Maintainability First
Automation ที่ดีต้อง:
- อ่านง่าย
- แยก layer ชัด
- ไม่ hard-code
- ใช้ Page Object
- แยก test data

Code test ก็ต้อง clean เหมือน production code

---

## 9️⃣ Anti-Patterns
- ใช้ sleep แก้ปัญหา
- Copy-paste test
- Locator fragile
- Hard-coded data
- Test พึ่งกันเอง

สิ่งนี้ทำให้ไฟล์ดู mature มาก

---

## 🔟 Automation as Engineering Discipline
Automation ไม่ใช่แค่ QA tool แต่มันคือ software engineering
- ต้องคิดเรื่อง architecture
- ต้องคิดเรื่อง CI/CD
- ต้องคิดเรื่อง scalability

---


## 1️⃣1️⃣ Automation Strategy in Real Projects
Automation ควรเริ่มจาก:
- วิเคราะห์ risk ของระบบ
- เลือก critical user flow ก่อน
- เริ่มจาก stable feature
- ค่อยขยาย coverage อย่างมีแผน
- integrate เข้ากับ CI pipeline

Automation ที่ดีคือการสร้างระบบ validation ที่เติบโตไปพร้อมกับ product

---

## Summary
Stability > Quantity
Maintainability > Complexity
Engineering Thinking > Tool Usage

> การมี Automation Mindset คือหัวใจของ QA ที่ทันสมัยและสร้างคุณค่าให้ทีม
