# 🛠 ENGi-Docker

## Build containers
```bash
docker compose build
```

## Run containers
```bash
docker compose up
```
หรือรันแบบ background:
```bash
docker compose up -d
```

## Stop containers
```bash
docker compose down
```
หรือหากต้องการลบ volumes (ระวังข้อมูลใน MariaDB จะหายด้วย):
```bash
docker compose down -v
```

## Check logs
ดู log ทั้งหมด:
```bash
docker compose logs -f
```

ดู log ของเฉพาะ backend:
```bash
docker compose logs -f backend
```

---

## 📌 หมายเหตุสำคัญ
- การใช้ `docker compose down -v` จะลบ **volume** ที่เก็บข้อมูลฐานข้อมูล **MariaDB** ด้วย ทำให้ข้อมูลทั้งหมดใน database หายไป!
- หากมีการแก้ไขไฟล์ source code (เช่น frontend/backend) ไม่จำเป็นต้อง rebuild container ทุกครั้ง เพราะใช้ `volumes` ในการ mount ไว้แล้ว
- ในกรณีที่มีการเปลี่ยนแปลง dependencies (เช่น `package.json` หรือ go module), ควรสั่ง `docker compose build` ใหม่
- สำหรับ frontend ที่ใช้ Vite ต้องแน่ใจว่า server bind เป็น `0.0.0.0` เพื่อให้สามารถเข้าจากภายนอก container ได้