# ระบบงานเลี้ยงรุ่น (Reunion Token)

เว็บไฟล์เดียว ไม่ต้องมี server ใช้ได้ 4 อย่าง

- สร้างบัตร QR ให้เพื่อนแต่ละคน (สมัครเองหรือสตาฟสร้างให้ทั้งรุ่นแล้วพิมพ์)
- สแกนบัตรเช็คอินเข้างาน
- สแกนเติม token
- สแกนตัด token (ไม่พอจะไม่ตัด)

## ใช้งานบน GitHub Pages

1. กด **Use this template** หรือ Fork repo นี้
2. Settings → Pages → Source: **GitHub Actions**
3. push ขึ้น `main` แล้วรอ Actions รัน จะได้ลิงก์ `https://<user>.github.io/<repo>/`
4. เปิดด้วย HTTPS เท่านั้น กล้องสแกนถึงจะทำงาน

## ตั้งค่า

แก้ที่ `CFG` ใน `index.html`

| ค่า | ความหมาย |
|---|---|
| `EVENT` | ชื่องาน แสดงบนบัตร |
| `PIN` | รหัสสตาฟ **เปลี่ยนก่อนใช้จริง** |
| `FIREBASE` | ใส่ config เพื่อให้หลายเครื่องใช้ข้อมูลร่วมกัน |

## ใช้หลายเครื่องพร้อมกัน (Firebase)

ถ้าไม่ตั้งค่า ข้อมูลจะอยู่ในเบราว์เซอร์เครื่องเดียว

1. สร้างโปรเจกต์ที่ https://console.firebase.google.com
2. Build → Firestore Database → Create database
3. Project settings → Your apps → Web → คัดลอก `firebaseConfig` ไปใส่ `CFG.FIREBASE`
4. Firestore → Rules → วางเนื้อหาจาก `firestore.rules` (แก้วันหมดอายุ) แล้ว Publish

## ทำงานร่วมกับเพื่อน

- เชิญเพื่อนเป็น Collaborator: Settings → Collaborators
- แตก branch แล้วเปิด Pull Request เมื่อแก้โค้ด
- ใช้ Issues แบ่งงาน เช่น หน้าตา, รายงาน, ทดสอบกล้อง

## ข้อควรระวัง

- PIN ตรวจฝั่งเบราว์เซอร์ เหมาะกับงานเพื่อนคืนเดียว ไม่เหมาะกับเงินจำนวนมาก
- ซ้อมสแกนจริงบนมือถือหลายรุ่นก่อนวันงาน
- หลังงานจบให้ปิด rules ของ Firestore
