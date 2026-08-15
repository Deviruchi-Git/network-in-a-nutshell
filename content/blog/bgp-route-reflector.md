---
title: "ชื่อบทความภาษาไทยได้"
date: 2026-08-15
tags:
  - BGP
  - Routing
---

ย่อหน้าแรก — จะถูกใช้เป็นคำโปรยในหน้ารวมบทความ

<!--more-->

## หัวข้อแรก

เนื้อหา...

mermaid
graph TD
    SW1["Switch-1"]
    SW2["Switch-2"]
    SW3["Switch-3"]
    SW4["Switch-4"]
    L3["Leaf-3<br/>VTEP"]
    Host1["Client<br/>VLAN10"]
    Host2["Client<br/>VLAN20"]

    SW1 --- SW2
    SW1 --- SW2
    SW1 --- L2
    SW1 --- SW3
    SW2 --- SW4
    SW3 --- SW4
    SW3 --- SW4
    Host1 --- SW3
    Host2 --- SW4
