# K-Drama Rating Prediction

วิชา 1145 201 คณิตศาสตร์สำหรับวิทยาการข้อมูล | Final Project

## คำถามวิจัย
ปัจจัยอะไรของซีรีส์เกาหลี (network, แนว, จำนวนตอน, ปีที่ฉาย ฯลฯ) ที่ทำนายคะแนนรีวิว (Score) ได้ดีที่สุด?

## Dataset
Top Korean Drama List (~1500) — สแครปจาก MyDramaList
ที่มา: [Kaggle - noorrizki](https://www.kaggle.com/datasets/noorrizki/top-korean-drama-list-1500)
จำนวน: 1,647 แถว, 12 คอลัมน์

## วิธีรัน
1. ดาวน์โหลด dataset จาก Kaggle (ลิงก์ด้านบน) วางเป็น `dataset.csv` ในโฟลเดอร์เดียวกับ notebook
2. เปิด `final_[StudentID].ipynb` ด้วย Jupyter หรือ Google Colab
3. รัน Restart Kernel + Run All

## สรุปผลลัพธ์หลัก
- CLO1 (PCA/SVD): metadata เชิงตัวเลขแยกได้เป็น 2 มิติหลัก (ความละเอียด tag/genre และขนาดโปรดักชัน) ต้องใช้ 5 PC ครอบคลุม ≥80% ของความแปรปรวน
- CLO2 (EDA + Stats): Network และ Genre มีผลต่อ Score อย่างมีนัยสำคัญทางสถิติ (ANOVA p<0.001, t-test p<0.001)
- CLO3 (Model): Random Forest และ Gradient Boosting ให้ผลดีที่สุด (Test R²≈0.40-0.43) เหนือกว่า Linear Regression ที่ overfit
- CLO4 (Cross-Validation): GradBoost เสถียรที่สุดจาก 5-fold CV (RMSE=0.402, std=0.019)

## ข้อจำกัด
- Selection bias จากผู้ใช้ MyDramaList ที่ rate เฉพาะเรื่องที่ดูจบ
- ไม่มีตัวแปรสำคัญ เช่น งบประมาณ, TV rating จริง, กระแสโซเชียล
