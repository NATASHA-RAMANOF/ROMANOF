# GROMANOF Creative Portfolio

เว็บไซต์ Portfolio แบบ Static พร้อมใช้งานสำหรับ GROMANOF

## ไฟล์สำคัญ
- `index.html` — หน้าเว็บหลัก
- `styles.css` — ดีไซน์ทั้งหมด
- `script.js` — เมนูมือถือ, ตัวกรองผลงาน, lightbox
- `assets/hero-banner.png` — ภาพที่ 1 จากผู้ใช้
- `assets/profile-image-2-placeholder.png` — ภาพชั่วคราวสำหรับช่องภาพที่ 2

## เปลี่ยนภาพโปรไฟล์
ในแพ็กเกจนี้ไม่มีไฟล์ "ภาพที่ 2" แยกต่างหาก จึงใช้ภาพครอปจากภาพที่ 1 เป็นตัวอย่างชั่วคราว
ให้เปลี่ยนไฟล์ `assets/profile-image-2-placeholder.png` เป็นภาพโปรไฟล์จริงของคุณ โดยคงชื่อไฟล์เดิมไว้

## เพิ่มผลงาน
เพิ่มภาพใน `portfolio/` แล้วเพิ่ม `<article class="work-card"...>` ใน `index.html`
ค่า `data-category` รองรับ `editing`, `graphic`, `banner`, `social`

## เปิดใช้งาน
ดับเบิลคลิก `index.html` หรืออัปโหลดทั้งโฟลเดอร์ไปยัง GitHub Pages, Netlify, Vercel หรือโฮสติ้งทั่วไปได้ทันที
