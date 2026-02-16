# 📊 การวิเคราะห์เปรียบเทียบ: VM vs Docker Deployment
## ENGSE207 - Week 6 N-Tier Architecture

**ชื่อ-นามสกุล:** [กรอกชื่อนักศึกษา]
**รหัสนักศึกษา:** [กรอกรหัส]
**วันที่:** 16 กุมภาพันธ์ 2026

---

## 1. ตารางเปรียบเทียบ Setup Process

| ขั้นตอน | Version 1 (VM) | Version 2 (Docker) |
|---------|----------------|-------------------|
| ติดตั้ง PostgreSQL | ติดตั้งด้วย apt install และตั้งค่า user/database เอง | ใช้ image postgres:alpine พร้อม environment variables |
| ติดตั้ง Node.js | ติดตั้ง node + npm แล้ว build project | ใช้ Dockerfile build อัตโนมัติ |
| ติดตั้ง Nginx | ติดตั้งผ่าน apt และแก้ config ใน /etc/nginx | ใช้ nginx:alpine และ mount config |
| Configure Database | สร้าง database และ user ด้วยคำสั่ง psql | กำหนดผ่าน POSTGRES_DB ใน docker-compose |
| Configure SSL | สร้าง certificate และ config nginx เอง | mount certificate และ config ผ่าน volume |
| Start Services | ใช้ systemctl start ทีละ service | docker compose up -d คำสั่งเดียว |
| **เวลาทั้งหมด** | ~30-45 นาที | ~5-10 นาที |

---

## 2. ตารางเปรียบเทียบ Resource Usage

| Resource | Version 1 (VM) | Version 2 (Docker) |
|----------|----------------|-------------------|
| Memory Usage | ใช้ RAM เต็ม VM (เช่น 1-2GB) | ใช้ตาม container จริง (~200-400MB) |
| Disk Usage | ใช้พื้นที่ OS + packages ทั้งหมด | ใช้เฉพาะ image + volume |
| CPU Usage | ทำงานเต็ม OS | ใช้เฉพาะ container |
| Startup Time | 1-2 นาที | 5-10 วินาที |

---

## 3. ข้อดีของ Docker Deployment

1. **Isolation:** แต่ละ service แยก container ไม่กระทบกัน

2. **Reproducibility:** ใช้ docker-compose.yml เดียวกัน deploy ได้เหมือนกันทุกเครื่อง

3. **Faster Deployment:** สั่ง `docker compose up -d` คำสั่งเดียวจบ

4. **Easy Scaling:** เพิ่ม replica ได้ง่าย

5. **Resource Efficiency:** ใช้ทรัพยากรน้อยกว่า VM

---

## 4. คำสั่งที่ใช้บ่อย (Quick Reference)

### ดู memory usage ของ Docker

```bash
docker stats --no-stream

ดู disk usage
docker system df

ดู container sizes
docker ps -s

ดู image sizes
docker images

ดู network
docker network ls
docker network inspect taskboard-network

```


---

## 📝 การส่งงานและเกณฑ์การให้คะแนน

### วิธีการส่งงานบน Git

```bash
ตรวจสอบว่าอยู่ใน project directory
cd ~/engse207/week6-ntier-docker

ตรวจสอบ status
git status

Add ไฟล์ทั้งหมด (ยกเว้น .env และ ssl keys)
git add .

Commit
git commit -m "Week 6: N-Tier Architecture with Docker (Version 2)"

สร้าง repository บน GitHub แล้ว push

git remote add origin https://github.com/Chanasorn179/week6-ntier-docker.git
git branch -M main
git push -u origin main