<!-- workshop-header -->
<img width="1347" height="127" alt="Coding Thailand 2026 header" src="https://github.com/user-attachments/assets/ba5cf267-f460-4fb0-b69b-c461ae061a3b" />

# 📝 Worksheet W2 — Data Collection Log

> **ทำในช่วง 10:30-12:00**
> บันทึก process ของการเก็บข้อมูล

---

## ข้อมูลทีม + Edge Impulse

- **ชื่อทีม:** _ถั่วคอนแวนต์_
- **Edge Impulse Project URL:**
  ```
  https://studio.edgeimpulse.com/studio/XXXXX
  ```

---

1. Setup Log
ก่อนเริ่มเก็บข้อมูล ทีมทำอะไรบ้าง?
เวลา	ทำอะไร	ผู้รับผิดชอบ
10:30	เชื่อมต่อเซนเซอร์ Motion และทดสอบค่า accel	North
10:35	ติดตั้งเซนเซอร์ที่ข้อมือและเช็คการอ่านค่า	ทีม Hardware
10:40	สร้างโฟลเดอร์ class: wrist / leg / ankle	ทีม Data
10:45	ทดลองเก็บ sample สั้นๆ เพื่อเช็ค label	ทุกคน
2. Data Collection Sessions
Session 1
เวลา: 11:00 ถึง 11:20
Class: wrist movement (ข้อมือ)
จำนวน samples ที่เก็บ: 120
สภาพแวดล้อม: ห้องเรียน แสงปกติ
ใครเป็นsubject?: นักเรียนชาย 2 คน
Variation ที่ลอง: หมุนข้อมือเร็ว/ช้า มุมต่างกัน
ปัญหาที่เจอ: สายเซนเซอร์หลวมบางช่วง

Edited
Session 2
เวลา: 11:30 ถึง 11:50 
Class: leg movement (ขา) 
จำนวน samples ที่เก็บ: 110 
สภาพแวดล้อม: ทางเดินหน้าห้อง 
ใครเป็น subject?: นักเรียนชายและหญิง 
Variation ที่ลอง: เดินช้า เดินเร็ว ยกขา 
ปัญหาที่เจอ: มี noise ตอนเดินแรง
 
⸻
 
Session 3
เวลา: 12:00 ถึง 12:20 
Class: ankle movement (ข้อเท้า) 
จำนวน samples ที่เก็บ: 115
สภาพแวดล้อม: ห้องเรียน + หน้าห้อง 
ใครเป็น subject?: นักเรียน 3 คน 
Variation ที่ลอง: ขยับข้อเท้า ซ้าย/ขวา เดิน 
ปัญหาที่เจอ: ตำแหน่งเซนเซอร์เลื่อนระหว่างเก็บข้อมูล

3.  Dataset Summary
Class	จำนวน Train	จำนวน Test	สัดส่วน Train:Test
Wrist	96	24	80:20
Leg	88	22	80:20
Ankle	92	23	80:20
รวม	276	69	80:20
เป้าหมายตาม W1: 100 samples × class ทำได้จริง: 115 samples × class ห่างจากเป้า: +15%

4.  Quality Check
☑ ทุก class มี samples ใกล้เคียงกัน (ไม่ต่างกันเกิน 20%) ☑ เก็บใน ≥2 สภาพแวดล้อม ☑ เก็บจาก ≥2 subjects ☑ มี variation ใน angle/distance/lighting ☑ ไม่มี mislabeled data ☑ Train:Test split = 80:20

---

5.  Reflection — สิ่งที่เรียนรู้
a) สิ่งที่ยากที่สุด:
การแยกค่าการเคลื่อนไหวของแต่ละตำแหน่งให้แตกต่างกันชัดเจน

b) ถ้าทำใหม่จะปรับอะไร:
เพิ่มจำนวนข้อมูล Train และปรับตำแหน่งเซ็นเซอร์ให้แน่นขึ้น

c) คาดการณ์: model จะ confuse class ไหนกับอะไรมากที่สุด?
ขา กับ ข้อเท้า เพราะมีรูปแบบการเคลื่อนไหวคล้ายกัน
---

## 📤 วิธี submit

```bash
git add worksheets/W2-data-collection-log.md
git commit -m "docs: data collection log เก็บได้ครบ X samples ใน Y session"
git push
```

---

## 💡 Best Practices

1. **อย่าเก็บข้อมูลที่ "สมบูรณ์แบบ" หมด** — โลกจริงไม่สมบูรณ์แบบ
2. **เก็บข้อมูล "เหมือนไม่ใช่ class ใดเลย" เป็นอีก class** = noise/background class
3. **สลับคนเก็บ** — กัน bias ของ subject เดียว
4. **เช็คตัวอย่างทุก 20 samples** — กัน mislabel
