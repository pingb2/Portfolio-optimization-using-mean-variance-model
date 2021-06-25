# Portfolio-optimization-using-mean-variance-model

การจัดพอร์ตลงทุนโดยใช้โมเดลค่าเฉลี่ยความแปรปรวน

ข้อมูลจากการทดสอบข้อมูลหุ้นในด้วยวิธีการใช้โมเดลค่าเฉลี่ยความแปรปรวน (Mean variance model) และการคำนวณผลตอบแทนต่อ 1 หน่วยความเสี่ยง (Sharpe ratio) โดยแต่ละโมเดลจะใช้ตัว Optimizer 2 ชนิด ได้แก่ Particle Swarm Optimization (PSO) และ Differential Evolution (DE) เพื่อเพิ่มประสิทธิภาพในการหาคำตอบ และ ผลตอบแทนที่ได้รับกลับคืนในตอนท้าย

วิธีการดำเนินงานสามารถแบ่งได้ออกเป็น 4 การทดลอง
1. Mean variance + PSO
2. Mean variance + DE
3. Sharpe ratio + PSO
4. Sharpe ratio + DE

โดยจะแบ่งตัว Train และ Test ในอัตรา 2:1 ให้ตัว Train นั้นมีจำนวนที่เยอะกว่า และตัว Test เป็นจำนวนที่น้อยกว่ารวมไปถึงข้อมูลที่ยังไม่เคยถูก Train

หลังทำการ Run Program ทั้งหมด ก็จะได้ค่า Weight (สัดส่วนของหุ้น) มาใช้งานในตัวของ Test และได้ผลรับค่า Return (ผลกำไร)
