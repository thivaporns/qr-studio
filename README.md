# QR Studio (Static Version) — สำหรับ GitHub Pages

เว็บสร้าง QR Code แบบ **HTML + JavaScript ล้วนๆ** ทำงานในเบราว์เซอร์ 100%
ไม่ต้องมีเซิร์ฟเวอร์ Python รองรับการโฮสต์บน **GitHub Pages** ได้ทันที

## ความสามารถ

- สร้าง QR จากข้อความ/ลิงก์ทั่วไป
- กำหนดสี QR / สีพื้นหลัง / ขนาดเอง
- ใส่โลโก้ตรงกลาง QR
- สร้าง QR จากลิงก์ไฟล์ (PDF/รูปภาพ) ที่คุณโฮสต์ไว้แล้วที่อื่น (Google Drive, Dropbox ฯลฯ)
- ดาวน์โหลด QR เป็น PNG

## ⚠️ ข้อจำกัดเทียบกับเวอร์ชัน Python/Flask

เวอร์ชันนี้ **ไม่มีเซิร์ฟเวอร์** จึงไม่สามารถ "อัปโหลดไฟล์ขึ้นเว็บแล้วสร้างลิงก์ให้อัตโนมัติ" ได้เหมือนเวอร์ชัน Flask
คุณต้องอัปโหลดไฟล์ PDF/รูปภาพไปยังบริการอื่นก่อน (เช่น Google Drive แล้วเปลี่ยนเป็น "ลิงก์แชร์แบบสาธารณะ")
จากนั้นนำลิงก์นั้นมาวางในแท็บ "ลิงก์ไฟล์" เพื่อสร้าง QR Code

## วิธีนำขึ้น GitHub Pages

### วิธีที่ 1: ผ่านเว็บ GitHub (ไม่ต้องใช้คำสั่ง)

1. สร้าง repository ใหม่บน GitHub เช่น `qr-studio`
2. อัปโหลดไฟล์ `index.html` เข้าไปใน repo (ปุ่ม **Add file → Upload files**)
3. ไปที่ **Settings → Pages**
4. ในหัวข้อ **Build and deployment** เลือก Source เป็น **Deploy from a branch**
5. เลือก branch `main` และ folder `/ (root)` แล้วกด **Save**
6. รอ 1-2 นาที เว็บจะขึ้นที่ `https://<username>.github.io/qr-studio/`

### วิธีที่ 2: ผ่าน Git command line

```bash
git init
git add index.html README.md
git commit -m "Initial commit: QR Studio static site"
git branch -M main
git remote add origin https://github.com/<username>/qr-studio.git
git push -u origin main
```

จากนั้นไปตั้งค่า GitHub Pages ตามขั้นตอนที่ 3-6 ด้านบน

## รันทดสอบในเครื่องก่อนขึ้นจริง

ไม่ต้องติดตั้งอะไรเลย แค่ดับเบิลคลิกเปิดไฟล์ `index.html` ด้วยเบราว์เซอร์ได้เลย
หรือถ้าต้องการรันผ่าน local server (บางฟีเจอร์ของเบราว์เซอร์ทำงานดีกว่าเมื่อรันผ่าน server):

```bash
python3 -m http.server 8000
```

แล้วเปิด `http://localhost:8000`

## โครงสร้างไฟล์

```
qr-static-site/
├── index.html    # ไฟล์เดียวจบ มี HTML + CSS + JavaScript ในตัว
└── README.md
```

## เทคโนโลยีที่ใช้

- HTML5 + CSS3
- JavaScript (Vanilla)
- ไลบรารี [qrcode.js](https://davidshimjs.github.io/qrcodejs/) โหลดผ่าน CDN (cdnjs.cloudflare.com) สำหรับสร้าง QR Code ฝั่งเบราว์เซอร์
