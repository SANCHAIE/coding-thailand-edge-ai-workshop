<!-- workshop-header -->
<img width="1347" height="127" alt="Coding Thailand 2026 header" src="https://github.com/user-attachments/assets/ba5cf267-f460-4fb0-b69b-c461ae061a3b" />

# 🎨 Day 1 Teaching Slides

> **25 สไลด์พร้อมใช้สำหรับ Day 1** — ใช้กับช่วง opening (09:00-09:30) และช่วง transition ตลอดวัน
>
> คัดลอกหัวข้อและข้อความแต่ละบล็อกไปวางใน Canva/PowerPoint/Google Slides ได้ทันที

---

## 📑 Section 1: Opening — 09:00-09:15

### Title
**Coding Thailand 2026 — Edge AI Workshop**
*Arduino UNO Q × Modulino × Edge Impulse*

- ชื่อ session / ชื่อผู้นำช่วง
- โลโก้ DEPA, Coding Thailand
- วันที่

---

### Welcome & House Rules

```
Welcome! 🎉

📋 กฎ:
1. มีคำถาม → ยกมือ ไม่ต้องรอ
2. ทำงานเป็นทีม — ไม่ใช่แข่งกันคนเดียว
3. ใช้เครื่องมือสมัยใหม่ — Git, Edge Impulse, AI helpers ได้ แต่อ้างอิงให้ชัด
4. ตั้งใจตลอด → 30 คะแนนรออยู่
```

---

### What is Edge AI?

```
Cloud AI 🌥️        →    Edge AI ⚡
─────────────       ─────────────
ส่งข้อมูลขึ้น cloud     ทำงานบนอุปกรณ์เลย
ช้า ต้องมีเน็ต          เร็ว ไม่ต้องเน็ต
แพง บน scale          ราคาถูก
Privacy?               Privacy ✓
```

ตัวอย่าง: Smart camera, Voice assistant, Fall detector, Quality control

---

### Why Arduino UNO Q?

```
UNO Q = สองสมองในบอร์ดเดียว

🧠 MCU side: real-time I/O (Modulino)
🐧 Linux side: รัน ML model ใหญ่ๆ ได้

→ ต่างจาก Arduino ทั่วไป
→ Powered by Qualcomm Dragonwing
```

---

### Modulino — Plug & Play

```
🔌 Qwiic connector — เสียบแล้วใช้ได้เลย
🚫 ไม่ต้องบัดกรี
🔗 Daisy-chain — ต่อกันเป็นสาย

11 modules ให้เลือก:
Sensors: Movement, Distance, Thermo, Light
Inputs: Buttons, Knob, Joystick
Outputs: Pixels, Buzzer, LED Matrix, Vibro
```

ใส่ภาพ Modulino kit

---

### Edge Impulse — The ML Platform

```
Pipeline ใน 4 ขั้นตอน:

1. 📥 Collect    — เก็บข้อมูลจาก sensor
2. 🧠 Design     — เลือก algorithm
3. 🏋️ Train     — สอน model
4. 📤 Deploy    — ใส่ลง UNO Q

ทำผ่าน web — ฟรี (free tier)
```

---

### Today's Goal

```
จบวันนี้ ทีมจะมี:

✅ AI model V1 + V2 (improved)
✅ Deploy บน UNO Q ทำงานจริง
✅ Prediction Log อย่างน้อย 10 cases
✅ GitHub repo ของทีม
✅ Idea Canvas สำหรับ Prototype Day
```

---

### 30-Point Skill Assessment

```
ประเมินตลอดวัน ที่ GitHub history คือหลักฐาน

Setup & Safety              5 pts
Core Implementation        10 pts  ★ มากสุด
Data & Testing              5 pts
Debug & Explain             5 pts
Participation               5 pts
─────────────────────────
Total                      30 pts
```

⚠️ ย้ำว่า process > result

---

## 📑 Section 2: Anchor Demo — 09:15-09:30

### Demo Setup — "Gesture Wand"

```
🪄 โจทย์: จำแนกท่าทางมือ

Classes:
○ วงกลม (Circle)
○ Z-shape
○ นิ่ง (Still)

Sensor: Modulino Movement (IMU)
Output: Modulino Pixels (สีตามคลาส)
```

สลับไป live demo

---

### Demo Step-by-Step (สำรองถ้า demo พัง)

```
1. ต่อ Modulino Movement → UNO Q (Qwiic)
2. เปิด Edge Impulse Studio
3. Connect device
4. Record: 20 samples × 3 classes
5. Generate features
6. Train (NN classifier, nano)
7. Build → Deploy to UNO Q
8. Demo inference 🎉
```

---

### Pipeline Summary

```
ไม่ว่า track ไหน — Pipeline เดียวกัน:

┌─────────┐    ┌──────────┐    ┌────────┐    ┌─────────┐
│ Collect │ → │ Train    │ → │ Deploy │ → │ Test    │
│ Data    │    │ Model    │    │ Model  │    │ + Iter. │
└─────────┘    └──────────┘    └────────┘    └─────────┘
   ↑                                              │
   └──────── เพิ่มข้อมูล/แก้ class ────────────────┘
```

---

### Q&A Break

```
มีคำถามตอนนี้ก่อนเริ่ม hands-on?

⏰ เหลือ 30 นาทีก่อนเลือก track
```

---

## 📑 Section 3: Setup Block — 09:30-10:00

### Step 1 — Boot UNO Q

```
1. เสียบ USB-C เข้า UNO Q
2. รอ ~30 วินาที (boot Linux)
3. เปิด Arduino App Lab
4. Login
5. เห็นบอร์ดในรายการ ✓
```

---

### Step 2 — Connect Modulino

```
⚠️ Qwiic polarized — เสียบผิดด้านเสียบไม่ได้

Order ที่แนะนำ:
UNO Q → Movement → Pixels → Buzzer

ทดสอบ: เปิด sample sketch
"ModulinoExamples/Movement/ReadAccelerometer"
```

---

### Step 3 — GitHub + Edge Impulse Setup

```
ทีมทำพร้อมกัน:

1. สร้าง repo ทีมใหม่จาก template ที่แชร์ไว้
2. Clone ลง laptop
3. แก้ README ใส่ชื่อทีม
4. Commit + Push แรก

5. สมัคร Edge Impulse → สร้าง project ทีม
6. ใส่ link ใน README ทีม
7. Commit + Push
```

---

## 📑 Section 4: Track Selection — 10:00-10:30

### 4 Tracks Overview

```
🎯 A: Motion  — Modulino Movement
🎯 B: Vision  — USB Webcam
🎯 C: Env.    — Thermo + Light + Distance
🎯 D: Audio   — USB Mic

ทุก track มี Basic / Intermediate / Advanced
ทุก track คะแนนเต็ม 30 เท่ากัน
```

---

### Class Design Workshop

```
ก่อนเริ่มเก็บข้อมูล ทุกทีมต้องตอบ:

❓ คลาสคืออะไรบ้าง?
❓ แต่ละคลาสต่างกันด้วยอะไร?
❓ Edge case ที่อาจสับสน?
❓ จำนวน samples ต่อ class?

→ เขียนใน worksheets/W1-class-design.md
→ Commit + Push
→ ให้ TA approve ก่อนเก็บจริง
```

---

## 📑 Section 5: Bias Awareness — แทรกตอน data collection

### AI Bias — เรื่องที่ต้องระวัง

```
ถ้าเก็บข้อมูล...

✗ Class A: ในห้องสว่าง
✗ Class B: ในห้องมืด

AI จะเรียนรู้: "แสง = ตัวแยกคลาส"
ไม่ได้เรียน object จริงๆ

→ ใช้ในห้องสว่างที่ไม่เคยเห็น → พังทันที
```

---

### Bias-Free Data Collection

```
หลักการ:
✅ Balanced     — แต่ละ class จำนวนใกล้กัน
✅ Diverse      — หลาย environment, มุม, แสง
✅ Representative — ใกล้กับที่ deploy จริง

ทดสอบ: "ถ้าคนอื่นลองใช้ — ยังทำงานได้ไหม?"
```

---

## 📑 Section 6: Training — 13:00-14:00

### Edge Impulse Settings

```
สำหรับ UNO Q:

⚙️ Model size: nano (2.4M)  ← สำคัญ!
⚙️ Processor: GPU
⚙️ Epochs: 30-50
⚙️ Learning rate: 0.0005

ถ้า memory error → ลด model size
ถ้า accuracy ต่ำ → ดูข้อมูล ก่อนเพิ่ม epochs
```

---

### อ่าน Confusion Matrix

```
              Predicted
              A    B    C
Actual  A   [40]   3    7    ← class A 80% accuracy
        B    2  [38]   10    ← class B confuse กับ C
        C    1    5  [44]

✓ Diagonal สูง = ดี
✗ Off-diagonal สูง = สับสน → แก้ data
```

---

### Deploy to UNO Q

```
ใน Edge Impulse:
1. Deployment → "Arduino UNO Q"
2. Build → Download

ใน Arduino App Lab:
3. Import model
4. Run on board

Test: ทดลอง inference จริง!
```

---

## 📑 Section 7: Iteration — 14:00-15:30

### 10-Case Testing

```
ทุกทีมต้องทดสอบ ≥10 cases

ใน Worksheet W3 บันทึก:
- Timestamp
- Input description
- Predicted class + confidence
- Actual class
- ถูก/ผิด

วิเคราะห์: case ไหนผิด? ทำไม?
```

---

### V1 → V2 Improvement

```
จาก analysis:

🔄 Iteration plan:
- เก็บข้อมูลเพิ่มในคลาสที่ผิดบ่อย
- เพิ่ม variation ของ environment
- (อาจ) แก้ class definition

Train V2 → Test → เปรียบเทียบ

📝 เขียนผลใน docs/v1-vs-v2.md
```

---

## 📑 Section 8: Wrap Up — 16:00-16:30

### Day 1 Closing

```
🎉 จบ Day 1!

Submission Checklist:
□ Repo มี commit ≥10
□ W1-W4 ครบ
□ Model V2 deploy ได้
□ Prediction Log ≥10 cases
□ Idea Canvas พร้อมไป Day 2

⏰ Day 2 (พรุ่งนี้): Prototyping
⏰ Day 3: Pitching (Student-Led!)

ลุยต่อ Day 2 กันครับ/ค่ะ 🙏
```

---

## 🎨 องค์ประกอบเวลาเอาไปทำสไลด์จริง

- **Theme color:** ตามโลโก้ Coding Thailand (เหลือง + ดำ + ขาว)
- **Font:** Sans-serif อ่านง่ายในระยะไกล (Inter / Roboto / Sukhumvit Set)
- **Code blocks:** Monospace + background สีเข้ม
- **Images:** ภาพ Modulino, UNO Q จริง — เอาจาก https://store.arduino.cc/
- **Diagrams:** ใช้ Excalidraw หรือ Mermaid

## 📦 เอาไปทำต่อใน Canva/Slides

แนะนำให้:
1. Copy deck นี้
2. ใช้ AI (เช่น Canva Magic Design หรือ Gamma) ช่วย generate ครั้งแรก
3. ปรับแต่งให้ตรงกับ branding ของ workshop
