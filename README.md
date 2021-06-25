# Portfolio-optimization-using-mean-variance-model

การจัดพอร์ตลงทุนโดยใช้โมเดลค่าเฉลี่ยความแปรปรวน

Library ที่จำเป็นจะต้องใช้กับการทำงาน

from pandas_datareader import data as web
import pandas as pd
import numpy as np

from numpy import random
from datetime import datetime
import matplotlib.pyplot as plt

ข้อมูลจากการทดสอบข้อมูลหุ้นในด้วยวิธีการใช้โมเดลค่าเฉลี่ยความแปรปรวน (Mean variance model) และการคำนวณผลตอบแทนต่อ 1 หน่วยความเสี่ยง (Sharpe ratio) โดยแต่ละโมเดลจะใช้ตัว Optimizer 2 ชนิด ได้แก่ Particle Swarm Optimization (PSO) และ Differential Evolution (DE) เพื่อเพิ่มประสิทธิภาพในการหาคำตอบ และ ผลตอบแทนที่ได้รับกลับคืนในตอนท้าย

วิธีการดำเนินงานสามารถแบ่งได้ออกเป็น 4 การทดลอง
1. Mean variance + PSO
2. Mean variance + DE
3. Sharpe ratio + PSO
4. Sharpe ratio + DE

Parameter ที่สามารถเปลี่ยนแปลงได้

assets                = สำหรับ List รายชื่อ หุ้นที่จะต้องการใช้งาน
stockStartDate        = กำหนดวันเริ่มต้นของช่วงข้อมูลที่จะทำการดึงข้อมูลจาก Yahoo Finance
stockEndDate          = กำหนดวันสุดท้ายของช่วงข้อมูลที่จะทำการดึงข้อมูลจาก Yahoo Finance

Mean variance
E_return              = Expect return ผลตอบแทนที่คาดหวัง

Sharpe Ratio
Rf_TH                 = Risk free rate อัตราผลตอบแทนที่ปราศจากความเสี่ยง ที่ใช้ 1.7 นั้นมาจาก ผลตอบแทนพันธบัตรไทย

PSO
Number of particle    = กลุ่มประชากรทั้งหมดที่มีในที่นี้เราใช้หุ้นจำนวน 30 ตัว
Iteration             = 150 จำนวนครั้งในการทำซ้ำ
weights_velo          = 0.9 -> 0.4  Weight velocities ใช้ในการควบคุมผลกระทบของความเร็วของการทำงานก่อนหน้า ซึ่งตัวนี้จะทำให้ Particle ของเราทั่งหมดได้รับการกำหนดค่าลง

ปรับความเร็ว
c1                    = 2.5 -> 0.5 Cognitive constant ความเชื่อมั่นของประชากรในแต่ละตัว
c2                    = 0.5 -> 2.5 Social constant ความเชื่อมั่นของประชากรในกลุ่ม

DE
Number of population  = กลุ่มประชากรทั้งหมดที่มีในที่นี้เราใช้หุ้นจำนวน 30 ตัว
Dimension             = 30  ความลึกของมิติในที่นี้จะใช้เป็นจำนวนของหุ้น 30 ตัว
Iteration             = 150 จำนวนครั้งในการทำซ้ำ
Mutation rate         = 0.5 อัตราปริมาณการเปลี่ยนข้อมมูลของ array
Crossover rate        = 0.9 อัตราปริมาณการ Crossover ของค่าข้อมูลใน array


โดยจะแบ่งตัว Train และ Test ในอัตรา 2:1 ให้ตัว Train นั้นมีจำนวนที่เยอะกว่า และตัว Test เป็นจำนวนที่น้อยกว่ารวมไปถึงข้อมูลที่ยังไม่เคยถูก Train

หลังทำการ Run Program ทั้งหมด ก็จะได้ค่า Weight (สัดส่วนของหุ้น) จากการ Train ข้อมูลในช่วงเวลาที่เรากำหนด มาใช้งานในตัวของ Test และได้ผลรับค่า Return (ผลกำไร)
