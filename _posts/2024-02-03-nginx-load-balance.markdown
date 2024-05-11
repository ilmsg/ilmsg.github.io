---
layout: post
title:  "Nginx load balance - round robin"
date:   2024-02-03 15:23:18 +0700
categories: nginx load balance
---

nginx ทำ load balance ด้วย round robin

ได้ยินมานานแล้ว เรื่องการทำ load balance เพื่อที่จะให้เว็บไซต์ของเรา รองรับการเข้าชมจากผู้ใช้งานจำนวนมาก

อย่างเช่น มีเครื่อง server สัก 3 เครื่องทำงานอยู่ ถ้ามีเครื่องไหนล่มไป ก็ยังเหลืออีก 2 เครื่องที่ยังทำงานได้ต่อ, ผู้ใช้งานก็ยังเข้าชมเว็บไซต์ได้ปกติ 

คำว่า round robin มันหมายถึง หมุนเป็นวงกลม แล้วตัว nginx proxy ก็ทำงานเป็นแบบนั้นเลย, user ที่เข้าเว็บมา จะเจอ nginx เป็นอันดับแรก และทำหน้าที่เป็น proxy พาไป server ที่ config เอาไว้แต่ละเครื่อง แล้วจะพาหมุนไปเรื่อยๆ, 1 คน(reqeust) ต่อ 1 เครื่อง เลย

เรารัน `docker compose up -d` ขึ้นมาแล้ว, เราก็เข้าหน้าเว็บ [http://webapp.local:3000](http://webapp.local:3000), [http://localhost:3000](http://localhost:3000) ได้เลย, แล้วกด(F5) refresh หน้าเว็บไซต์, เราจะได้ผลลัพธ์ key ว่ามาจากเครื่องไหน, สังเกตุได้ว่า key จะเปลี่ยนหมุนวนไปเรื่อยๆ

![https://github.com/ilmsg/nginx-load-balance/blob/main/images/2023-12-29_130616.png?raw=true](https://github.com/ilmsg/nginx-load-balance/blob/main/images/2023-12-29_130616.png?raw=true)

![https://github.com/ilmsg/nginx-load-balance/blob/main/images/2023-12-29_130629.png?raw=true](https://github.com/ilmsg/nginx-load-balance/blob/main/images/2023-12-29_130629.png?raw=true)

![https://github.com/ilmsg/nginx-load-balance/blob/main/images/2023-12-29_130638.png?raw=true](https://github.com/ilmsg/nginx-load-balance/blob/main/images/2023-12-29_130638.png?raw=true)

ตัวอย่างที่ทำ มีเครื่องมือที่ใช้เป็น docker, nginx, golang

[https://github.com/ilmsg/nginx-load-balance](https://github.com/ilmsg/nginx-load-balance)
