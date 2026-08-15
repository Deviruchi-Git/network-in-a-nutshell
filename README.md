# Network in a Nutshell

บันทึกสรุปความเข้าใจเรื่อง network — สร้างด้วย [Hugo](https://gohugo.io/) + ธีม [Hextra](https://imfing.github.io/hextra/) และ deploy อัตโนมัติผ่าน GitHub Pages

## โครงสร้างไฟล์

```
├── hugo.yaml                   ตั้งค่าเว็บทั้งหมด (ชื่อเว็บ เมนู ธีม)
├── i18n/th.yaml                คำแปลไทยของปุ่มต่างๆ ในธีม
├── content/
│   ├── _index.md               หน้าแรก
│   ├── about.md                หน้าเกี่ยวกับ
│   └── blog/                   ← บทความอยู่ที่นี่ เพิ่มไฟล์ .md ได้เลย
│       ├── _index.md           หน้ารวมรายการบทความ
│       ├── hello.md
│       └── vxlan-evpn.md
├── go.mod / go.sum             ระบุเวอร์ชันธีมที่ใช้ (ไม่ต้องแก้)
└── .github/workflows/pages.yaml  สคริปต์ build อัตโนมัติ (ไม่ต้องแก้)
```

## เขียนบทความใหม่

สร้างไฟล์ `.md` ใหม่ใน `content/blog/` แล้วขึ้นต้นด้วยบล็อกนี้:

```markdown
---
title: "ชื่อบทความ"
date: 2026-08-20
tags:
  - BGP
  - Routing
---

ย่อหน้าแรก จะถูกใช้เป็นคำโปรยในหน้ารวมบทความ

<!--more-->

เนื้อหาที่เหลือ...
```

ส่วนระหว่าง `---` เรียกว่า **front matter** คือข้อมูลกำกับบทความ ไม่ใช่เนื้อหา

| ช่อง | จำเป็น | หมายเหตุ |
| --- | --- | --- |
| `title` | ✅ | ครอบด้วย `"` เสมอ กัน error ถ้ามี `:` ในชื่อ |
| `date` | ✅ | รูปแบบ `YYYY-MM-DD` — ใช้เรียงลำดับบทความ |
| `tags` | ไม่ | ขึ้นบรรทัดใหม่ นำหน้าด้วย `-` |
| `draft` | ไม่ | ใส่ `draft: true` = ยังไม่เผยแพร่ |

## เผยแพร่

push ขึ้น branch `main` แล้วรอประมาณ 1-2 นาที GitHub Actions จะ build และ deploy ให้เอง

ดูสถานะได้ที่แท็บ **Actions** ของ repo — ✅ เขียว = ขึ้นเว็บแล้ว, ❌ แดง = มีอะไรผิด กดเข้าไปอ่าน log ได้

## ตั้งค่าครั้งแรก

1. Settings → Pages → Source เลือก **GitHub Actions**
2. แก้ `USERNAME` ใน `go.mod` และ `content/about.md` ให้เป็น GitHub username ของคุณ
3. (ถ้าต้องการ) เปิด `editURL` และเมนู GitHub ใน `hugo.yaml`
