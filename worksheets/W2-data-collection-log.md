<!-- workshop-header -->
<img width="1347" height="127" alt="Coding Thailand 2026 header" src="https://github.com/user-attachments/assets/ba5cf267-f460-4fb0-b69b-c461ae061a3b" />

# 📝 Worksheet W2 — Data Collection Log

> **ทำในช่วง 10:30-12:00**
> บันทึก process ของการเก็บข้อมูล

---

## ข้อมูลทีม + Edge Impulse

- **ชื่อทีม:** S.R.I. Miracle
- **Edge Impulse Project URL:**
  ```
  https://studio.edgeimpulse.com/studio/XXXXX
  ```

---

## 1. Setup Log

ก่อนเริ่มเก็บข้อมูล ทีมทำอะไรบ้าง?

| เวลา | ทำอะไร | ผู้รับผิดชอบ |
|---|---|---|
| 09:30 |ศึกษา learning block ต่างๆ |ธีรภัทร|
| 10:35 |ศึกการนำsensorมาเชื่อมกับedge impulse| ณิชาภัทร|
| | | |

---

## 2. Data Collection Sessions

บันทึกแต่ละ session การเก็บข้อมูล:

### Session 1

- **เวลา:**  10:30 ถึง 11:30
- **Class:**  bottle
- **จำนวน samples ที่เก็บ:** 50รูป
- **สภาพแวดล้อม:** ผ้าปูโต๊ะห้องประชุม/กำเเพงห้อง
- **ใครเป็น subject?:** ขวดน้ำ
- **Variation ที่ลอง:** different angle and distance
- **ปัญหาที่เจอ:** เอไอเข้าใจผิด คิดว่าพื้นหลังขวดน้ำเป็นส่วนหนึ่งของข้อมูลด้วย

### Session 2

- **เวลา:** 11:30ถึง12:30
- **Class:**paper 
- **จำนวน samples ที่เก็บ:** 50
- **สภาพแวดล้อม:** ผ้าปูโต๊ะห้องประชุม/กำเเพงห้อง
- **ใครเป็น subject?:** paper
- **Variation ที่ลอง:** different angle and distance
- **ปัญหาที่เจอ:** -

### Session 3

- **เวลา:** 13:30 ถึง 14:30
- **Class:** box
- **จำนวน samples ที่เก็บ:** 50
- **สภาพแวดล้อม:** ผ้าปูโต๊ะห้องประชุม/กำเเพงห้อง
- **ใครเป็น subject?:** box
- **Variation ที่ลอง:** different angle and distance
- **ปัญหาที่เจอ:** -


---

## 3. Dataset Summary

| Class | จำนวน Train | จำนวน Test | สัดส่วน Train:Test |
|---|---|---|---|
| | | | |
| | | | |
| | | | |
| **รวม** | | | |

**เป้าหมายตาม W1:** _______ samples × class
**ทำได้จริง:** _______ samples × class
**ห่างจากเป้า:** _______%

---

## 4. Quality Check

ตอบทุกข้อก่อนเริ่ม train:

- [ yes ] ทุก class มี samples ใกล้เคียงกัน (ไม่ต่างกันเกิน 20%)
- [ yes ] เก็บใน ≥2 สภาพแวดล้อม
- [ yes ] เก็บจาก ≥2 subjects (Vision/Audio/Motion ที่มีคน)
- [ yes ] มี variation ใน angle/distance/lighting
- [ yes ] ไม่มี mislabeled data (เช็คตัวอย่างแล้ว)
- [ yes ] Train:Test split = 80:20

---

## 5. Reflection — สิ่งที่เรียนรู้

### a) สิ่งที่ยากที่สุด:
```
[การ train model ให้มีความเเม่นยำมากที่สุด ]
```

### b) ถ้าทำใหม่จะปรับอะไร:
```
[เปลี่ยนsample ให้ตรงกับสิ่งที่ model ต้องการมากขึ้น เช่น
-ลดสิ่งรบกวนของsample
-ถ่ายในมุมเดียวกัน เเละเเสงเท่ากัน
-ใช้sample ที่มากกว่านี้ เพื่อให้เกิดความหลากหลายเเละความละเอียดของข้อมูล
-เราเช็คsample น้อยเกินไป]
```

### c) คาดการณ์: model จะ confuse class ไหนกับอะไรมากที่สุด?
```
[class:ขวดน้ำ เนื่องจากเป็นขวดที่มีลักษณะใส ทำให้modelเกิดการสับสนกับพื้นหลัง-สิ่งเเวดล้อม]
```

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
