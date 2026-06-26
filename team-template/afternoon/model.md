<!-- workshop-header -->
<img width="1347" height="127" alt="Coding Thailand 2026 header" src="https://github.com/user-attachments/assets/ba5cf267-f460-4fb0-b69b-c461ae061a3b" />

# Afternoon — Model

- **Input ที่ใช้:** Image
- **Classes:** 2 class Hand/Face
- **จำนวนตัวอย่าง/class:** 60
- **วิธีเชื่อมเข้า Edge Impulse:** [✅] กล้อง (`edge-impulse-linux`)  [ ] Modulino (`data-forwarder`)

## V1
- Accuracy (ใน Studio): 88%
- F1 score ราย class (class : F1): Face 59% Hand 50%
- class ที่ F1 ต่ำสุด:Hand 50%
- รูป Confusion Matrix: [Confusion-Matrix](../../Depa_image/AI/Confusion-Matrix.png)
- อ่านแล้วเห็นอะไร (class ไหนสับสนกับ class ไหน): -

## V2 (ถ้าทัน)
- แก้อะไรจาก V1: _______________
- Accuracy V2: ____  | ดีขึ้น/แย่ลงตรงไหน: _______________

## รันบนบอร์ด
- [✅] วิธีรัน: [ ✅] กล้อง/ → `edge-impulse-linux-runner` (Web UI :4912)  [ ] Modulino → Arduino library ในสเก็ตช์
- [✅] ป้อน input จริงแล้ว prediction เปลี่ยนตาม (inferencing time: 15-40 ms)
- คลิป/รูปตอนรัน: [Face](../..Depa_image/AI/Face.jpg)
- คลิป/รูปตอนรัน:[Hand](../..Depa_image/AI/Hand.jpg)

## (ต่อยอด) Output logic
- threshold ที่ใช้: confidence ≥ -
- map class → output:"เตือน" → Buzzer + Pixels แดง
