
# 📚 แผนการเรียน QA 

---

## 🎯 ตารางการเรียนรู้

| เรียนอะไร                        | อ่านจากไหน                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | เรียนได้อะไร                                                                                       |
| -------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| **เริ่มต้น: เข้าใจ QA** 🌱       | 1. [QA Big Picture & Principles](01-qa-fundamentals/01.%20QA%20Big%20Picture%20&%20Principles.md)<br>2. [SDLC & STLC Framework](01-qa-fundamentals/02.%20SDLC%20&%20STLC%20Framework.md)<br>3. [Quality & Risk Thinking](01-qa-fundamentals/03.%20Quality%20&%20Risk%20Thinking.md)<br>4. [Verification vs Validation](01-qa-fundamentals/04.%20Verification%20vs%20Validation.md)                                                                                                                                                                                                                 | เข้าใจว่า QA คืออะไร ทำงานยังไง และมีขั้นตอนไหนบ้าง                                                |
| **วิเคราะห์ Requirement** 📋     | 1. [Requirement Analysis](02-qa-process/01-requirement-analysis/01.%20Requirement%20Analysis.md)<br>2. [Acceptance Criteria (AC)](02-qa-process/01-requirement-analysis/02.%20Acceptance%20Criteria%20(AC).md)<br>3. [Impact Analysis](02-qa-process/01-requirement-analysis/03.%20Impact%20Analysis.md)                                                                                                                                                                                                                                                                                           | อ่าน requirement ให้เข้าใจ, แยก AC ออกมา, วิเคราะห์ผลกระทบเมื่อมีการเปลี่ยน                        |
| **เทคนิคออกแบบ Test** 🎨         | 1. [Design Techniques Overview](03-design-techniques/00.%20Design%20Techniques%20Overview.md)<br>2. [Equivalence Partitioning (EP)](03-design-techniques/01-black-box/01.%20Equivalence%20Partitioning%20(EP).md)<br>3. [Boundary Value Analysis (BVA)](03-design-techniques/01-black-box/02.%20Boundary%20Value%20Analysis%20(BVA).md)<br>4. [Decision Table](03-design-techniques/01-black-box/03.%20Decision%20Table.md)                                                                                                                                                                        | รู้จักเทคนิคต่างๆ แล้วเลือกใช้ให้ถูกจังหวะ (เช่น EP, BVA, Decision Table)                          |
| **ออกแบบและเขียน Test Case** ✍️  | 1. [Test Case Design](02-qa-process/02-test-design-data/01.%20Test%20Case%20Design.md)<br>2. [Test Case Writing](02-qa-process/02-test-design-data/02.%20Test%20Case%20Writing.md)<br>3. [Test Data Strategy](02-qa-process/02-test-design-data/03.%20Test%20Data%20Strategy.md)<br>4. [Test Data Design](02-qa-process/02-test-design-data/04.%20Test%20Data%20Design.md)<br>5. [Traceability Matrix (RTM)](02-qa-process/02-test-design-data/05.%20Traceability%20Matrix%20(RTM).md)<br>6. [Test Case Review Process](02-qa-process/02-test-design-data/06.%20Test%20Case%20Review%20Process.md) | เขียน test case ให้ชัดเจนจนคนอื่นทำตามได้, เตรียม test data, ทำ RTM เพื่อเช็คว่าครบทุก requirement |
| **รัน Test และสรุปรายงาน** ▶️    | 1. [Test Execution Result](02-qa-process/04-test-reporting/01.%20Test%20Execution%20Result.md)<br>2. [Test Run & Summary Report](02-qa-process/04-test-reporting/03.%20Test%20Run%20&%20Summary%20Report.md)<br>3. [Go & No-Go Criteria](02-qa-process/04-test-reporting/04.%20Go%20&%20No-Go%20Criteria.md)                                                                                                                                                                                                                                                                                       | รู้ว่าต้องทำ Smoke/Sanity/Regression เมื่อไหร่, รัน test แล้วบันทึกผลและสรุปรายงาน                 |
| **จัดการ Bug** 🐛                | 1. [Bug Management Overview](02-qa-process/03-defect-management/01.%20Bug%20Management%20Overview.md)<br>2. [Anatomy of Bug Report](02-qa-process/03-defect-management/02.%20Anatomy%20of%20Bug%20Report.md)<br>3. [Severity vs Priority](02-qa-process/03-defect-management/05.%20Severity%20vs%20Priority.md)<br>4. [Defect Life Cycle](02-qa-process/03-defect-management/06.%20Defect%20Life%20Cycle.md)<br>5. [Root Cause Analysis (RCA)](02-qa-process/03-defect-management/08.%20RCA%20(Root%20Cause%20Analysis).md)                                                                        | เขียน bug report ให้ชัดเจน, แยก Severity กับ Priority ให้ออก, ลองหาสาเหตุของ bug ด้วย RCA          |
| **Templates และ Cheatsheets** 📝 | 1. [Test Case Template](06-templates-cheatsheets/test-case-template.md)<br>2. [Bug Report Template](06-templates-cheatsheets/bug-report-template.md)<br>3. [Test Summary Report Template](06-templates-cheatsheets/test-summary-report-template.md)<br>4. [SQL Cheatsheet](06-templates-cheatsheets/sql-cheatsheet.md)<br>5. [API Testing Checklist](06-templates-cheatsheets/api-testing-checklist.md)                                                                                                                                                                                            | Template พร้อมใช้สำหรับการทำงานจริง                                                                |
| **ทักษะด้านเทคนิค** 🛠️          | _กำลังเพิ่มเติมอยู่_<br>- SQL สำหรับ QA<br>- ทดสอบ API ด้วย Postman<br>- Automation ด้วย Playwright                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | สกิลเทคนิคที่ต้องใช้ในการทำงานจริง                                                                 |
| **ฝึกจากของจริง** 💼             | - อ่าน bug report จริงๆ มาวิเคราะห์ดู<br>- หาโปรเจกต์มาลองเขียน test case เล่นจริงๆ<br>- ลองทำ automation กับโปรเจกต์ง่ายๆ (Todo, E-commerce)                                                                                                                                                                                                                                                                                                                                                                                                                                                      | เอาเรื่องที่เรียนมาไปลองทำจริงๆ                                                                    |

---

## � รายละเอียดทั้งหมด

### 🌱 เริ่มต้น: พื้นฐาน QA
- **01. QA Big Picture & Principles** - QA คืออะไร, 7 หลักการสำคัญ
- **02. SDLC & STLC Framework** - วงจร Software Development และ Testing
- **03. Quality & Risk Thinking** - คิดเรื่องคุณภาพและความเสี่ยงยังไง
- **04. Verification vs Validation** - V&V ต่างกันยังไง

### ⚙️ ขั้นตอนการทำงาน QA
- **Requirement Analysis** - วิเคราะห์ Requirement, AC, Impact Analysis
- **Test Design & Data** - ออกแบบ Test Case, เขียน Test Case, เตรียม Test Data, RTM, Review
- **Defect Management** - จัดการ Bug, เขียน Bug Report, Severity/Priority, Life Cycle, RCA
- **Test Reporting** - บันทึกผลการทดสอบ, สรุปรายงาน, Go/No-Go

### 🎨 เทคนิคการออกแบบ Test
- **Black-box** - EP, BVA, Decision Table, State Transition
- **White-box** - Statement & Decision Coverage
- **Experience-based** - Error Guessing, Exploratory Testing, Checklist-based

### 🛠️ ทักษะด้านเทคนิค
- **SQL for QA** - ตรวจสอบข้อมูล, query, join
- **API Testing** - Postman, REST API, automation
- **Test Automation** - Playwright, Selenium, POM
- **Locator Strategy** - วิธีเลือก locator ให้ stable, maintainable, performance-aware
- **POM Best Practices** - ออกแบบ Page Object Model ให้ scalable, readable, maintainable

### 📝 Templates และ Cheatsheets
- **Templates** - Test Case, Bug Report, Test Summary Report
- **Cheatsheets** - SQL Cheatsheet, API Testing Checklist

### 📦 ตัวอย่างและสถานการณ์จริง
- **Examples** - ตัวอย่าง Test Case, Decision Table, Bug Report จากสถานการณ์จริง
- **Practice** - โปรเจกต์ตัวอย่างและสถานการณ์สำหรับฝึกหัด


---
## 💡 สิ่งที่เรียนรู้และต้องยึดถือ (Key Mindsets) 

* ❓ **ถามทันทีเมื่อ Requirement ไม่ชัด** — อย่าเดาเอาเอง การดักบั๊กตั้งแต่แรก คุ้มกว่าตามแก้ทีหลัง
* ✍️ **เขียน Test Case ให้เคลียร์** — ผู้อื่นสามารถนำไปรันและได้ผลลัพธ์แบบเดียวกัน (Reproducible) 
* 🔧 **หมั่นลงมือทำจริง (Hands-on)** — ฝึกเขียน SQL, ยิง Postman และลองใช้ Playwright สม่ำเสมอ
* 🐛 **วิเคราะห์หาสาเหตุที่แท้จริงของ Bug (Root Cause)** — ไม่ใช่แค่เจอแล้วจบ แต่ต้องแกะให้รู้ว่ามันพังมาจากจุดไหน
* 🤖 **เข้าใจ Concept ก่อนเริ่ม เขียน Automation** — เข้าใจ Flow การทำงานและ Manual Test ให้แน่นก่อนแปลงเป็นสคริปต์ 
* 📊 **เลือกใช้ Test Design Techniques ให้คุ้มค่า** — ใช้ BVA, EP และ Decision Table เพื่อดักจับบั๊กสูงสุดในเวลาที่จำกัด 
* 🎯 ****แยก Severity กับ Priority ให้ออก**** — มองความเสียหายทางเทคนิค (_Severity_) กับความเร่งด่วนทางธุรกิจ (_Priority_) แยกจากกันเสมอ

---


