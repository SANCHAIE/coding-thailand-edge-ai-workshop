<!-- workshop-header -->
<img width="1347" height="127" alt="Coding Thailand 2026 header" src="https://github.com/user-attachments/assets/ba5cf267-f460-4fb0-b69b-c461ae061a3b" />

# Team XX — Edge AI Workshop Day 1

> **วิธีส่งงาน:** Fork repo นี้ → กรอกช่องด้านล่าง → commit (ดู [student/05-submit.md](../student/05-submit.md))
> กรอกแค่ที่ขีดเส้นใต้ ขอ **ครบ** ดีกว่าสวย

## 👥 ข้อมูลทีม
- **ชื่อทีม:** Absolute evolution
- **เลขทีม:** XX
- **ชื่อบอร์ด:** ARDUINO UNO Q
- **สมาชิก + บทบาท (3H):**
  - 🛠️ **Hacker** (เทคนิค: ต่อบอร์ด/เก็บ data/train/deploy): ฮานีฟ
  - 🎨 **Hipster** (ผู้ใช้: output ที่คนเข้าใจ/รูปแบบใช้งาน):อัซรอน,ฟาเดียร์
  - 📣 **Hustler** (คุณค่า: ปัญหา/ผู้ใช้/เล่าเดโม่): อัซรอน,ฟาเดียร์

## ✅ Checklist

**ก่อนเริ่ม**
- [✅ ] **Fork repo ทีม** (ทำก่อนเลย จะได้กรอกงานทั้งวัน) → [student/05-submit.md](../student/05-submit.md) ข้อ 1

**เช้า — ทำให้ UNO Q อยู่มือ**
- [✅ ] เช็กอุปกรณ์ที่ได้รับครบ → [morning/kit-checklist.md](morning/kit-checklist.md)
- [✅ ] ตั้งบอร์ดเป็นของทีม (รหัส/ชื่อ/Wi-Fi) → [student/02-setup-board.md](../student/02-setup-board.md)
- [✅ ] ต่อ input + ลอง Modulino 7 ตัว + challenges → [morning/hardware-check.md](morning/hardware-check.md)

**บ่าย — เทรนจริง**
- [✅ ] input ที่เลือกเทรน: ฝาขวด,ขวดน้ำ
- [✅ ] เทรน V1 + อ่าน F1/confusion matrix → [afternoon/model.md](afternoon/model.md)
- [✅ ] deploy ลงบอร์ดรันได้ (รูป/คลิปใน `assets/`)
- [ ✅] prediction log ≥10 cases → [afternoon/predictions.csv](afternoon/predictions.csv)

**ต่อยอด — ไอเดียนวัตกรรม**
- [ ✅] Lean Canvas 4 ช่องแรก → [idea-canvas.md](idea-canvas.md)

## 📝 ตอบสั้น 3 ข้อ (ปิดวัน)
**1. ทีมสอน AI ให้ทำอะไร? (ปัญหา + ผู้ใช้)** ให้จำแนกประเภทระหว่างขวดกับฝาขวด 
**2. model ทำได้ดีแค่ไหน F1 ต่ำสุดที่ class ไหน ผิดเพราะอะไร?** model ยังทำได้ไม่ดีสุด F1 ที่ต่ำสุดในคลาสของฝาขวด เพราะรูปภาพตัวอย่างมี bias
**3. ถ้ามีเวลาอีก 1 ชม. จะแก้อะไรก่อน?** จะแก้การเทรนโมเดลเอไอใหม่ให้ดีกว่าเดิม

## 🔗 ลิงก์
- Edge Impulse project: https://l.facebook.com/l.php?u=https%3A%2F%2Fstudio.edgeimpulse.com%2Fstudio%2F1040466%2Facquisition%2Ftraining%3Fpage%3D1%26fbclid%3DIwZXh0bgNhZW0CMTEAc3J0YwZhcHBfaWQPNDM3NjI2MzE2OTczNzg4AAEekzFJY3LqXbtaZRekcw2gf6093gPgDNf_uzokU7T_3VDhVROwSM-HxtQEdYs_aem_1Dd4OvExnIEz4aOPvs8mJg&h=AUBeZEFhayUCjwMssZJcM4hZAAOnOQTd3RVmxcXgqJLrQHXUFz7z61_5eJA5i68LeuHnsuUOyzhsTr6lGSwyxVO9bjUuDgEGxALPpKl14ZctNDepnboBAXtasAk2z3XgdJXBd0ihY554Whc&s=1
- รูป/คลิป model รันบนบอร์ด: ดูใน [assets/](assets/)

## 📦 ในโฟลเดอร์นี้มีอะไร
| ไฟล์ | กรอกตอนไหน |
|---|---|
| [morning/kit-checklist.md](morning/kit-checklist.md) | ก่อนเริ่ม — เช็กอุปกรณ์ที่ได้รับ |
| [morning/hardware-check.md](morning/hardware-check.md) | เช้า — ต่อ input + ลอง Modulino |
| [afternoon/model.md](afternoon/model.md) | บ่าย — ผลเทรน + deploy |
| [afternoon/predictions.csv](afternoon/predictions.csv) | บ่าย — ทดสอบ 10 cases |
| [idea-canvas.md](idea-canvas.md) | ท้ายวัน — ไอเดียต่อยอด |
| [assets/](assets/) | รูป/คลิปหลักฐานทั้งหมด |
