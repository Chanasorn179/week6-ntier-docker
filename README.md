# 🐳 WEEK 6 - N-Tier Architecture with Docker

โปรเจกต์นี้เป็นส่วนหนึ่งของรายวิชา **ENGSE207 Software Architecture**  
โดยพัฒนาระบบด้วยแนวคิด **N-Tier Architecture** ร่วมกับ **Docker**

---

## 📌 แนวคิดของระบบ

**N-Tier Architecture** คือการแบ่งระบบออกเป็นหลายชั้น (Layers) เพื่อให้แยกหน้าที่ชัดเจน ได้แก่:

- 🌐 Presentation Layer (Controller / API)
- ⚙️ Business Logic Layer (Service)
- 🗄️ Data Access Layer (Database)

และใช้ **Docker** เพื่อรันแต่ละส่วนใน container แยกกัน  
ช่วยให้ deploy และจัดการระบบได้ง่ายขึ้น  [oai_citation:0‡クラスメソッド発「やってみた」系技術メディア | DevelopersIO](https://dev.classmethod.jp/articles/command-docker-basic-to-use/?utm_source=chatgpt.com)  

---

## 🧱 Architecture Overview

```
Client → API → Service → Database
             ↑
          Docker
```

### 🔑 แนวคิดสำคัญ

- แยก Layer ชัดเจน (Separation of Concerns)
- ใช้ Docker container สำหรับแต่ละ service
- รองรับการขยายระบบ (Scalable)
- ลดปัญหา environment ไม่ตรงกัน

---

## 📁 โครงสร้างโปรเจกต์

```
week6-ntier-docker/
├── frontend/        ← (ถ้ามี)
├── backend/
│   ├── controllers/
│   ├── services/
│   ├── repositories/
│   └── models/
├── database/
├── docker-compose.yml
└── Dockerfile
```

---

## ⚙️ Features

- 🏗️ โครงสร้างแบบ N-Tier
- 🐳 ใช้ Docker ในการรันระบบ
- 🔗 เชื่อมต่อหลาย service ผ่าน docker-compose
- 📦 แยก container แต่ละส่วนของระบบ

---

## 👥 สมาชิกในทีม

- นายเบญจศรายุทธ น้อยอุบล  
- นายชนสรณ์ บุตรถา   
- นายธาวัน ทิพคุณ  
- นายอดิ โรจน์ กุหลั่น  

---

## 🚀 วิธีใช้งานโปรเจกต์

### 1. Clone Repository

```bash
git clone https://github.com/Chanasorn179/week6-ntier-docker.git
```

### 2. เข้าไปที่โฟลเดอร์

```bash
cd week6-ntier-docker
```

---

## ▶️ Run ด้วย Docker

```bash
docker compose up --build
```

---

## 📊 ตรวจสอบ Container

```bash
docker compose ps
```

---

## 🌐 เข้าใช้งานระบบ

```
http://localhost:3000
```

(หรือ port ตามที่กำหนดใน docker-compose)

---

## 🛠️ เทคโนโลยีที่ใช้

- Docker 🐳
- Docker Compose
- N-Tier Architecture
- Backend Framework (Node.js / Java)
- Database (MySQL / PostgreSQL)

---

## 📦 จุดเด่นของโปรเจกต์

- แยก Layer ชัดเจน
- ใช้ Docker ทำให้ Deploy ง่าย
- ลดปัญหา dependency
- รองรับการขยายระบบในอนาคต

---

## ⚠️ ข้อจำกัด

- ต้องเข้าใจ Docker เพิ่ม
- มีความซับซ้อนมากกว่า Monolith
- ต้องจัดการหลาย container

---

## 📊 เปรียบเทียบกับ Week 5

| Feature | Client-Server | N-Tier |
|---|---|---|
| Structure | 2 Layer | Multiple Layers |
| Scalability | Medium | Higher |
| Maintainability | Medium | High |

---

## 📖 สิ่งที่ได้เรียนรู้

- การออกแบบระบบแบบ N-Tier
- การใช้ Docker และ Docker Compose
- การแยก Layer ของระบบ
- การจัดการหลาย Service

---

## 📎 Repository
https://github.com/Chanasorn179/week6-ntier-docker
