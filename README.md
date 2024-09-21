IP Server http://13.229.123.224/
1. ทำการเข้าไปที่ AWS และเลือกหัวข้อEC2 
2. จากนั้นทำการสร้าง Instances
3. เลือก OS ที่ต้องการ[Ubuntu]
4. จากนั้นทำการ Deploy โดยการนำsource code เข้าไปใน Instancesที่สร้างเพื่อเตรียมในการ Deploy
5. ทำการสร้าง Dockerfile โดยใน file ประกอบไปด้วย
--Dockerfile--
FROM oven/bun
COPY . .
RUN bun install
CMD ["bun", "run", "start"]
6. หลังจากนั้น build container โดยใช้
คำสั่ง
sudo docker build -t lastes .
7. run container โดยการ map port 80 ของเครื่อง server กับ port 3000 ภายใน container โดยใช้
คำสั่ง
sudo docker run -d -p 80:3000 lastes



