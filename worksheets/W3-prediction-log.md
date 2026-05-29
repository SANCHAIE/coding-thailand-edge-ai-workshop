<!-- workshop-header -->
<img width="1347" height="127" alt="Coding Thailand 2026 header" src="https://github.com/user-attachments/assets/ba5cf267-f460-4fb0-b69b-c461ae061a3b" />

# 📝 Worksheet W3 — Prediction Log

> **ทำในช่วง 14:00-15:30**
> ⭐ บันทึกให้เห็นว่า model พลาดตรงไหนจริง และทีมตัดสินใจ iterate จากอะไร

---

## ข้อมูลทีม

- **ชื่อทีม:** เหล่ามากับดวง
- **Model Version ที่ทดสอบ:** ☑ V1 (ทดสอบครั้งแรก)  ☑ V2 (หลัง iterate)

---

## V1 — Test ครั้งแรก (อย่างน้อย 10 cases)

### Setup

- **เวลาเริ่มทดสอบ:** 14:00
- **เวลาเสร็จ:** 14:30
- **Model link ใน Edge Impulse:** `https://studio.edgeimpulse.com/studio/654321/deployment`
- **สภาพแวดล้อมที่ทดสอบ:** ห้องเรียน แสงไฟนีออน และทดลองย้ายไปหน้าต่างที่มีแสงย้อนบางกรณี
- **Output ที่ใช้ทดสอบ:** Modulino Pixels (สีเขียว/เหลือง/แดง) + ลำโพง/Buzzer แจ้งเตือน
- **Threshold ที่ใช้ (ถ้ามี):** Confidence $\ge 0.80$ ถึงจะยอมรับว่าเป็นบุคคลนั้น
### Prediction Log V1

| # | Case ที่ทดสอบ | Predicted Class | Confidence | Response Time | Output/Action | Actual Class | ถูก/ผิด | หมายเหตุ |
|---|---|---|---|---|---|---|---|---|
| 1 || 1 | Staff A ยืนหน้าตรง ระยะ 1 เมตร | Authorized_Staff | 0.94 | 45 ms | Pixels เขียว | Authorized_Staff | ✅ ถูก | แม่นยำและตอบสนองไว |
| 2 | Staff B หันซ้าย-ขวา ช้าๆ | Authorized_Staff | 0.82 | 48 ms | Pixels เขียว | Authorized_Staff | ✅ ถูก | ค่ามั่นใจลดลงเล็กน้อยเมื่อเอียงหน้า |
| 3 | คนแปลกหน้า (Stranger) เดินผ่านหน้ากล้อง | Stranger | 0.88 | 42 ms | Pixels เหลือง + Beep | Stranger | ✅ ถูก | ระบบคัดกรองได้ถูกต้อง |
| 4 | ฉากห้องว่าง ไม่มีคนอยู่ | No_Face | 0.98 | 40 ms | ปิดไฟ Pixels | No_Face | ✅ ถูก | พื้นหลังไม่มีสัญญาณรบกวน |
| 5 | Staff A ใส่ผ้าปิดปาก (Mask) เดินเข้ามา | Stranger | 0.72 | 52 ms | Pixels เหลือง + Beep | Authorized_Staff | ❌ ผิด | โมเดลสับสนเพราะเครื่องแต่งกายบดบังใบหน้า |
| 6 | ใช้รูปถ่ายของ Staff A บนจอมือถือส่องกล้อง | Authorized_Staff | 0.85 | 45 ms | Pixels เขียว | Blacklist | ❌ ผิด | เกิด Spoofing กล้องแยกไม่ออกระหว่างภาพจริงกับภาพถ่าย |
| 7 | คนแปลกหน้าสวมแว่นตากันแดด | No_Face | 0.61 | 55 ms | ปิดไฟ Pixels | Stranger | ❌ ผิด | โมเดลหาดวงตาไม่เจอ เลยมองไม่เป็นใบหน้าคน |
| 8 | ลายเสื้อยืดที่เป็นรูปใบหน้าการ์ตูน | No_Face | 0.91 | 42 ms | ปิดไฟ Pixels | No_Face | ✅ ถูก | โมเดลคัดกรอง False Positive ได้ดี |
| 9 | Staff C ยืนในมุมมืดย้อนแสงริมหน้าต่าง | Stranger | 0.65 | 50 ms | Pixels เหลือง + Beep | Authorized_Staff | ❌ ผิด | แสงย้อนทำให้ Features บนใบหน้ามืดเกินไป |
| 10 | บุคคลในกลุ่ม Blacklist เดินเข้ามาตรงๆ | Blacklist | 0.83 | 47 ms | Pixels แดง + ไซเรน | Blacklist | ✅ ถูก | ตรวจจับและแจ้งเตือนได้ถูกต้องตามเงื่อนไข |

### V1 Summary

| Metric | ค่า |
|---|---|
| Total cases | 10 |
| Correct | 6 |
| Wrong | 4 |
| **Accuracy** | 60.00% |
| Average confidence (ถูก) | 0.89 |
| Average confidence (ผิด) | 0.71 |
| Average response time | 46.60 ms |

### Confusion Pattern V1

ระบุ pattern ที่ผิด:

```
1."การบดบังใบหน้า (Mask/แว่นกันแดด)" ถูกจัดเป็น "Stranger" หรือ "No_Face" เนื่องจากสูญเสียตำแหน่งดวงตาและปาก
2. "รูปภาพจากหน้าจอมือถือ" ถูกจัดเป็น "Authorized_Staff" (Spoofing อัตราผ่านสูงถึง 85%) เนื่องจากโมเดล 2D โฟกัสแค่ลวดลายใบหน้า
3."สภาวะย้อนแสง (Backlight)" ทำให้ระบบจำแนก Staff เป็น คนแปลกหน้า (Stranger) เพราะสีผิวและมิติของเงาเปลี่ยนไป
```

---

## 🔄 Iteration Plan — แก้อะไรใน V2?

จาก V1 analysis จะปรับอะไร? (ทำได้หลายข้อ)

- [ ] เก็บข้อมูลเพิ่มใน class ที่ผิดบ่อย
  - **Class:** `Authorized_Staff` และ `Stranger`
  - **จำนวน:** 100 samples samples
  - **Variation ใหม่:** ถ่ายภาพเพิ่มในสภาวะใส่ Mask, ใส่แว่นตา, และจุดอับแสง/ย้อนแสง
- [ ] แก้ class definition
  - **Class:** _________________
  - **แก้เป็น:** _________________

- [ ] เพิ่ม class ใหม่
  - **Class:** _________________
  - **เหตุผล:** _________________

- [ ] ปรับ model parameter
  - **Parameter:** Neural Network Architecture & Augmentation
  - **จาก:**MobileNetV2 0.35 (No Augmentation) **เป็น:** MobileNetV2 0.35 พร้อมเปิดใช้งาน Data Augmentation (Random Brightness / Crop) ใน Edge Impulse เพื่อแก้ปัญหามุมมองและแสง

- [ ] อื่นๆ: ปรับซอฟต์แวร์โค้ดฝั่ง Output โดยเพิ่มเงื่อนไขว่า ค่า Confidence ของ Staff ต้อง $\ge 0.88$ เท่านั้น (จากเดิม 0.80) เพื่อลดอัตราการโดนหลอกด้วยรูปภาพปลอม (Anti-spoofing เบื้องต้น)
### Hypothesis

```
เราคาดว่าหลัง iterate แล้ว accuracy จะเพิ่มจาก 60% เป็น 85%
เพราะ การทำ Data Augmentation ด้านแสง (Brightness) จะช่วยให้โมเดลทนทานต่อจุดย้อนแสง และการเพิ่ม Threshold ฝั่ง Code จะช่วยสกัดรูปภาพปลอมบนมือถือที่มีค่า Confidence คาบลูกคาบดอกไม่ให้ผ่านเข้าคลาส Staff ได้
```

---

## V2 — Test หลัง iterate

### Prediction Log V2

ใช้ test cases เดิม + เพิ่ม 5 cases ใหม่ที่ท้าทาย

| # | Case ที่ทดสอบ | Predicted | Confidence | Response Time | Output/Action | Actual | ถูก/ผิด | เทียบกับ V1 |
|---|---|---|---|---|---|---|---|---|
| 1 | Staff A ยืนหน้าตรง ระยะ 1 เมตร | Authorized_Staff | 0.96 | 45 ms | Pixels เขียว | Authorized_Staff | ✅ ถูก | ☑ ดีขึ้น ☐ เท่าเดิม ☐ แย่ลง |
| 2 | Staff B หันซ้าย-ขวา ช้าๆ | Authorized_Staff | 0.89 | 47 ms | Pixels เขียว | Authorized_Staff | ✅ ถูก | ☑ ดีขึ้น ☐ เท่าเดิม ☐ แย่ลง |
| 3 | คนแปลกหน้า (Stranger) เดินผ่านหน้ากล้อง | Stranger | 0.91 | 42 ms | Pixels เหลือง + Beep | Stranger | ✅ ถูก | ☑ ดีขึ้น ☐ เท่าเดิม ☐ แย่ลง |
| 4 | ฉากห้องว่าง ไม่มีคนอยู่ | No_Face | 0.99 | 40 ms | ปิดไฟ Pixels | No_Face | ✅ ถูก | ☐ ดีขึ้น ☑ เท่าเดิม ☐ แย่ลง |
| 5 | Staff A ใส่ผ้าปิดปาก (Mask) เดินเข้ามา | Authorized_Staff | 0.81 | 54 ms | Pixels เขียว | Authorized_Staff | ✅ ถูก | ☑ ดีขึ้น ☐ เท่าเดิม ☐ แย่ลง |
| 6 | ใช้รูปถ่ายของ Staff A บนจอมือถือส่องกล้อง | Stranger | 0.74 | 46 ms | Pixels เหลือง (บล็อกผ่าน) | Blacklist | ❌ ผิด | ☑ ดีขึ้น ☐ เท่าเดิม ☐ แย่ลง (Conf ลดลงจนไม่ผ่าน Staff) |
| 7 | คนแปลกหน้าสวมแว่นตากันแดด | Stranger | 0.80 | 52 ms | Pixels เหลือง + Beep | Stranger | ✅ ถูก | ☑ ดีขึ้น ☐ เท่าเดิม ☐ แย่ลง |
| 8 | ลายเสื้อยืดที่เป็นรูปใบหน้าการ์ตูน | No_Face | 0.94 | 42 ms | ปิดไฟ Pixels | No_Face | ✅ ถูก | ☐ ดีขึ้น ☑ เท่าเดิม ☐ แย่ลง |
| 9 | Staff C ยืนในมุมมืดย้อนแสงริมหน้าต่าง | Authorized_Staff | 0.88 | 49 ms | Pixels เขียว | Authorized_Staff | ✅ ถูก | ☑ ดีขึ้น ☐ เท่าเดิม ☐ แย่ลง |
| 10 | บุคคลในกลุ่ม Blacklist เดินเข้ามาตรงๆ | Blacklist | 0.89 | 46 ms | Pixels แดง + ไซเรน | Blacklist | ✅ ถูก | ☑ ดีขึ้น ☐ เท่าเดิม ☐ แย่ลง |
| 11 | [New] คนแปลกหน้าสวมทั้ง Mask และแว่นตา | No_Face | 0.75 | 56 ms | ปิดไฟ Pixels | Stranger | ❌ ผิด | new case (ข้อมูลถูกบังมากเกินไป) |
| 12 | [New] สมาชิก Staff เดินเข้าหากล้องอย่างรวดเร็ว | Authorized_Staff | 0.84 | 45 ms | Pixels เขียว | Authorized_Staff | ✅ ถูก | new case |
| 13 | [New] รูปภาพหน้าจอมือถือของคนแปลกหน้า | Stranger | 0.87 | 44 ms | Pixels เหลือง | Stranger | ✅ ถูก | new case |
| 14 | [New] Staff ยืนซ้อนกัน 2 คนในกล้อง | Authorized_Staff | 0.82 | 58 ms | Pixels เขียว (จับคนหน้า) | Authorized_Staff | ✅ ถูก | new case |
| 15 | [New] นำรูปภาพ Blacklist ปริ้นท์ใส่กระดาษมาส่อง | Stranger | 0.71 | 46 ms | Pixels เหลือง | Blacklist | ❌ ผิด | new case (แยกกระดาษกับตัวจริงยาก) |

### V2 Summary

| Metric | V1 | V2 | Δ |
|---|---|---|---|
| Accuracy |60.00% |80.00% | +20.00% |
| Avg confidence (ถูก) | 0.89 | 0.90 | +0.01 |
| Avg confidence (ผิด) | 0.71 | 0.73 | +0.02 |
| Avg response time | 46.60 ms | 47.20 ms | +0.60 ms |
---

## 📊 Comparison V1 vs V2

ตอบเป็นข้อความ:

### ดีขึ้นเพราะอะไร?
```
ผลลัพธ์ดีขึ้นอย่างเห็นได้ชัดจากการเปิดฟังก์ชัน Data Augmentation ใน Edge Impulse (ช่วยแก้ปัญหาย้อนแสงใน Case 9) และการเพิ่มภาพถ่ายตอนใส่ Mask/แว่นตา ทำให้โมเดลเรียนรู้โครงสร้างรอบดวงตาและหน้าผากเพื่อระบุตัวตนได้แม้จะโดนบังไปครึ่งหน้า นอกจากนี้การปรับเพิ่ม Threshold ข้อมูลฝั่งซอฟต์แวร์บอร์ดช่วยสกัดกั้นการโกงด้วยภาพถ่ายจอมือถือของสตาฟได้ดีขึ้น (เปลี่ยนจากทายถูกเป็นสตาฟปลอม กลายเป็นทายว่าเป็นคนแปลกหน้า ซึ่งปลอดภัยกว่าเดิม)
```

### แย่ลงตรงไหน? (ถ้ามี)
```
Response Time เฉลี่ยเพิ่มขึ้นเล็กน้อยประมาณ 0.6 ms เนื่องจากโมเดลต้องประมวลผลกับภาพที่มีความซับซ้อนเพิ่มขึ้น และหากกรณีที่ Subject ใส่เครื่องประดับปิดบังมากเกินไป (ทั้งแว่นและ Mask พร้อมกันใน Case 11) โมเดลจะตัดสิทธิ์มองเป็นวัตถุสิ่งของทันที (No_Face) ซึ่งส่งผลให้เกิด False Negative
```

### ถ้ามีเวลาอีก จะทำ V3 ยังไง?
```
หากมีเวลาพัฒนาต่อในเวอร์ชัน V3 ทางทีมจะปรับไปใช้โครงสร้างโมเดลที่เป็น Object Detection ร่วมกับ Face Landmark (เช่น การใช้ชุดคำสั่งจากคอมพิวเตอร์ภายนอกร่วมกับบอร์ด) เพื่อทำการตรวจจับการเคลื่อนไหวเชิงลึกแบบ 3D (Liveness Detection) เช่น บังคับให้ผู้ใช้งานต้องกะพริบตาหรือหันหัวก่อนระบบจะส่งสัญญาณอนุมัติ เพื่อแก้ปัญหาการนำรูปภาพบนกระดาษหรือจอมือถือมาส่องหลอกระบบ (Anti-Spoofing) ได้อย่างเด็ดขาด
```

---

## 📤 วิธี submit

```bash
git add worksheets/W3-prediction-log.md
git commit -m "test: เพิ่ม prediction log V1 และ V2, accuracy เพิ่มจาก X% เป็น Y%"
git push
```

แนะนำให้ commit ครั้งหลัง V1 เสร็จ และอีกครั้งหลัง V2 เสร็จ (จะได้มี history ที่ดี)

---

## 💡 Tips

1. **ตอบตรงๆ ว่าโมเดลพลาดตรงไหน** — โฟกัส insight มากกว่าการทำตัวเลขให้ดูสวย
2. **บันทึก confidence** เสมอ — บอกได้ว่าโมเดลแน่ใจหรือเดา
3. **Edge cases** สำคัญกว่า normal cases — มันคือที่ทดสอบ robustness
4. **ถ้า V2 แย่กว่า V1** — เป็นเรื่องปกติ! บอก hypothesis ว่าทำไม จะได้คะแนนเต็มเหมือนกัน
5. **ถ้ารันแล้วค้าง ช้า หรือ output แกว่ง** — จดไว้ด้วย เพราะนี่คือหลักฐานของความเสถียร
