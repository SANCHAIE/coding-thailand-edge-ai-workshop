<!-- workshop-header -->
<img width="1347" height="127" alt="Coding Thailand 2026 header" src="https://github.com/user-attachments/assets/ba5cf267-f460-4fb0-b69b-c461ae061a3b" />

# Afternoon — Model

- **Input ที่ใช้:** ขวด,ฝา
- **Classes:** bottlePGA
- **จำนวนตัวอย่าง/class:** 20,30
- **วิธีเชื่อมเข้า Edge Impulse:** [✅ ] กล้อง/ไมค์ (`edge-impulse-linux`)  [ ] Modulino (`data-forwarder`)

## V1
- Accuracy (ใน Studio): 50.0
- F1 score ราย class (class : F1): 0.67,0.00
- class ที่ F1 ต่ำสุด: PGA
- รูป Confusion Matrix: ![50be1af977f20b63894862458cb29eac.jpeg](team-template/assets/50be1af977f20b63894862458cb29eac.jpeg)
- อ่านแล้วเห็นอะไร (class ไหนสับสนกับ class ไหน): AI สับสนระหว่าง class Bottle กับ class PGA

## V2 (ถ้าทัน)
- แก้อะไรจาก V1: _______________
- Accuracy V2: ____  | ดีขึ้น/แย่ลงตรงไหน: _______________

## รันบนบอร์ด
- [ ] วิธีรัน: [ ✅] กล้อง/ไมค์ → `edge-impulse-linux-runner` (Web UI :4912)  [ ] Modulino → Arduino library ในสเก็ตช์
- [ ] ป้อน input จริงแล้ว prediction เปลี่ยนตาม (inferencing time: 128 ms)
- คลิป/รูปตอนรัน: ![cb5eff11623c0fd43a17af1422f08362.jpeg](team-template/assets/cb5eff11623c0fd43a17af1422f08362.jpeg)

## (ต่อยอด) Output logic
- threshold ที่ใช้: confidence ≥ ____
- map class → output: _______________ (เช่น "เตือน" → Buzzer + Pixels แดง)
