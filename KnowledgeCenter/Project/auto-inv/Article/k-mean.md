K-Means Clustering
===

K-means คือ วิธีการหนึ่งใน Data mining อยู่ในกลุ่มของ Unsupervised Learning หรือแปลตรงๆคือการเรียนรู้แบบไม่ต้องสอน (Supervised Learning ต้องสอนก่อนต้องจับ Train และต้อง Test เป็นต้น) โดยหน้าที่หลักของ K-means คือการแบ่งกลุ่ม แบบ Clustering ซึ่งการแบ่งกลุ่มในลักษณะนี้จะใช้พื้นฐานทางสถิติ ซึ่งแน่นอนว่าต้องมีตัวเลขประกอบ อย่างน้อย 2 ตัวแปรขึ้นไปครับ

ผมยกตัวอย่างดังนี้ครับนึกถึงคนเราที่มีน้ำหนักและส่วนสูงเราสุ่มคนจำนวน 5,000 คนจะพบว่าแต่ละคนมีความแตกต่างกันและเราจะทำการแบ่งกลุ่มคนใน 5,000 คนนี้ด้วยปัจจัยคือน้ำหนักและส่วนสูงเราสามารถใช K-means ในการแบ่งกลุ่มให้ได้เป็นต้น

![](https://www.softnix.co.th/wp-content/uploads/2018/09/Screen-Shot-2561-09-06-at-10.51.38.png)

ความยากคือการเลือกจำนวนกลุ่มหรือค่า K ครับว่าจะเอากี่กลุ่มดีอันนี้ไม่ตายตัวมันขึ้นอยู่กับเราเลยว่าเราอยากได้กี่กลุ่มแล้วมันตอบโจทย์ผลลัพท์เราหรือไม่

**วิธีการของ K-means**

K-means มี 4 ขั้นตอนดังนี้ครับ

1.  กำหนดจำนวนกลุ่มขึ้นมาก่อนเช่น 2 กลุ่มหรือหมายความว่าค่า K=2 (กำหนดเป็น C1 และ C2) และสุ่มตำแหน่งแกน x,y ให้กับ C1 และ C2 จะได้ C1(x1,y1) และ C2(x2,y2)
2.  ดูตำแหน่งของสมาชิกแต่ละสมาชิกว่าอยู่ใกล้ใครมากกว่ากันก็ให้คนนั้นเป็นสมาชิกของ C นั้น จากตรงนี้เราจะรู้แล้วว่าสมาชิกแต่ละคนอยู่ในกลุ่มใดระหว่าง C1 และ C2
3.  ปรับ x,y ของ C1 และ C2 ใหม่ให้อยู่ตรงกลางของกลุ่ม
4.  ทำ ตามข้อ 2 และข้อ 3 อีกครั้งจนกว่า C1 และ C2 ตำแหน่งไม่เปลียน

หากไม่เข้าใจไม่เป็นไรครับ ขออธิบายแบบนี้ เริ่มเราเข้ามาในห้องๆหนึ่งมีคนอยู่ 100 คน ให้ทุกคนยืนอยู่ในตำแหน่งใดก็ได้และห้ามขยับ

นำคนมาอีกสองคนชื่อ นาย C1 และ นาย C2 เดินไปจุดใดของห้องก้ได้ครับ ให้ C1 ถามทุกคนว่า ใครใกล้ C1 มากกว่า C2 ยกมือขึ้น เมื่อ C1 เห็นคนที่ยกมือแล้ว C1 ก็จะเดินไปตรงกลางของกลุ่ม C2 ก็เช่นกันเดินไปกลางของกลุ่มคนที่ไม่ยกมือ เสร็จแล้ว C1 ก็ถามคำถามเดิมว่าใครใกล้ C1 ยกมือ (ตอน C1 เดินเข้าไปตรงกลางกลุ่มย่อมเดินออกห่างใครบางคนในกลุ่ม) และ C1 ก็ปรับตำแหน่งตัวเองเดินไปตำแหน่งที่ตรงกลางอีกครั้ง C2 ก็ทำเช่นกัน ทำอย่างนี้จน C1 และ C2 ไม่ขยับ เราจะได้กลุ่ม 2 กลุ่ม Cluster ด้วย K-means ครับ

**แล้วไงต่อ?**

ท่านอาจสงสัยว่าหลังจากได้ Group แล้วเกิดอะไรขึ้นต่อจากนี้ คำตอบคือ มันขึ้นอยู่กับ Characteristic ของแต่ละข้อมูลซึ่งไม่เหมือนกันครับ เช่นเราอาจเห็น Anomaly ว่า เอ ทำไม group นี้มีสมาชิกอยู่แค่ 2-3 คน และสมาชิกนี้อยู่ไกลเพื่อนมากๆ แสดงว่าคนนี้อาจไม่ได้เป็นคนปรกติทั่วไปก็เป็นได้(อาจเป็นมนุษต่างดาวปลอมตัวมาครับ 555)

รูป 1 รูปแทนคำล้านคำมาดูรูปกันดีกว่าครับ ก่อนอื่น สุ่ม C1 และ C2 ขึ้นมา ยืนตรงไหนก็ได้

![](https://www.softnix.co.th/wp-content/uploads/2018/09/Kmeans-Explain-Page-1.jpg)

หลังจากนั้นถามเพื่อนๆว่าใครใกล้ฉันมากที่สุดยกมือขึ้น

![](https://www.softnix.co.th/wp-content/uploads/2018/09/Kmeans-Explain-Page-2.jpg)

และ C1 กับ C2 ก็ย้ายไปตรงกลางของวง

![](https://www.softnix.co.th/wp-content/uploads/2018/09/Kmeans-Explain-Copy-of-Page-2.jpg)

ถามเพื่อนๆใหม่ครับว่าใครอยู่ใกล้ฉันยกมือขึ้นจะเห็บว่าสมาชิกเริ่มเปลี่ยนกลุ่ม

![](https://www.softnix.co.th/wp-content/uploads/2018/09/Kmeans-Explain-Page-4.jpg)

ย้ายไปอยู่ตรงกลางอีกครั้งและยกมือใหม่

![](https://www.softnix.co.th/wp-content/uploads/2018/09/Kmeans-Explain-Copy-of-Page-4.jpg)

ถึงตรงนี้คงไม่มีย้ายไปใหนอีกแล้วครับ ยกมือยังไงก็ได้เท่าเดิมเราจะสรุปได้ 2 กลุ่มดังรูปด้านบน ในเรื่องการตีความหมาย ขึ้นอยู่กับข้อมูลครับว่าข้อมูลอธิบายเป็นอย่างไรเช่น กลุ่มสีเขียวด้านบนหากแกน y คือน้ำหนัก เราจะแบ่งกลุ่มคนได้ 2 กลุ่มคือกลุ่มที่น้ำหนักน้อย และกลุ่มที่น้ำหนักมาก เราอาจนำข้อมูลดังกล่าวไปเพื่อทำ Marketing ให้กับกลุ่มคนที่น้ำหนักมากโดยใส่ Marketing การขายยาลดน้ำหนักให้กับกลุ่มคนกลุ่มนี้ได้ อันนี้ก็เป็นตัวอย่างหนึ่ง ดังรูปต่อไปนี้

![](https://www.softnix.co.th/wp-content/uploads/2018/09/screen-shot-2561-09-06-at-10.51.38.png)

จากรูปเป็นกลุ่มตัวอย่างข้อมูลน้ำหนักจากเว็บ kaggle สามารถ download ได้จาก  [DataSet](https://www.kaggle.com/yersever/500-person-gender-height-weight-bodymassindex)  ชุดนี้ เราทำการลากเส้นเพื่อแบ่ง Zone ที่มีน้ำหนักและความสูงอยุ่ในช่วงที่เป็นปรกติและผิดปรกติจะเห็นได้ว่ากลุ่ม Zone A ซึ่งเป็นกลุ่มที่ส่วนสูงไม่มาก(เตี้ย) แต่มีน้ำหนักมากคือกลุ่มที่มีน้ำหนักมากกว่าปรกติ และ Zone C ซึ่งเป็นกลุ่มที่รูปร่างสูงแต่น้ำหนักน้อย เราสามารถ Focus ไปยังกลุ่มคนที่อยู่ใน Zone A นั่นก็คือกลุ่มคนที่อยู่ใน Cluster กลุ่มสีเขียว เพื่อทำ Marketing ส่งPromotion ลดน้ำหนักให้กับลูกค้ากลุ่มนี้ได้

**มีตัวอย่างอื่นอีกมั้ย?**

ผมได้เตรียมอีกตัวอย่างหนึ่งเป็น Data เกี่ยวกับ Network เพื่อจะหา Anomaly หรือสิ่งผิดปรกติโดยมี Data คือ Bandwidth ของเครื่อง Server เครื่องหนึ่ง ในเวลา 8 โมง – 10 โมง

![](https://www.softnix.co.th/wp-content/uploads/2018/09/Screen-Shot-2561-09-06-at-14.06.05-1024x194.png)

แกน X คือเวลา 8 โมงถึง 10 โมงส่วนแกน Y คือปริมาณ Traffic ที่ใช้ไป พบว่าโดยปรกติแล้ว Bandwidth ไม่ควรถูกใช้มากแต่ช่วง 09:40 ถึง 09:50 มี Traffic ผิดปรกติ

**แล้ว K-means ช่วยได้อย่างไร?**

เรานำ History ของ 8 โมงมาเปรียบเทียบกับ 9 โมงครับ หาก Graph มันทับซ้อนกันได้พอดีก็แสดงว่าปรกติแต่หาก ไม่ทับซ้อนกันก็แสดงว่า Pattern ผิดปรกติ Data set ดังรูปด้านล่างคือตัวอย่าง Data set ที่เตรียมจะนำเข้า K-means

![](https://www.softnix.co.th/wp-content/uploads/2018/09/Screen-Shot-2561-09-06-at-14.38.59-104x300.png)

เมื่อใช้ K-means แล้วผลปรากฏดังรูปถัดไป

![](https://www.softnix.co.th/wp-content/uploads/2018/09/Screen-Shot-2561-09-06-at-14.40.51.png)

เมื่อกำหนดค่า K = 3 เราจะเห็นว่า Cluster กลุ่มสีแดงคือ ค่า Data ที่ผิดปรกติและแตกต่างจากกลุ่มในส่วนนี้เราสามารถนำผลการ Detect ไปสร้าง Alarm หรือ Notify ให้กับ Team NOC ได้ครับว่าเกิดเหตุการณ์ผิดปรกติเกิดขึ้น

**ตั้งว่าเกิน 20MB แล้ว Alert ก็ได้ ทำให้ยุ่งยากไปทำไม?**

บางทีเราอาจสงสัยว่ามันจะต่างจากการตั้ง Threshold ยังไง เช่นหากเกิน 20MB ให้ Alert ไป NOC แต่จริงๆแล้ว Pattern ของแต่ละช่วงเวลาไม่เหมือนกันครับ เช่นพฤติกรรมตอนกลางวันจะมี traffic ใช้มาก และกลางคืน ไม่มีใครใช้เลย การตั้ง Condition แบบตายตัวย่อมทำไม่ได้ การดูจาก Pattern ในอดีตจึงเป็นวิธีที่ดีวิธีหนึ่ง และด้วยพฤติกรรมของแต่ละองค์กร นั้นย่อมไม่เหมือนกันการหาก Anomaly ย่อมมี Pattern ไม่เหมือนกันแต่ K-means ถ้าเห็นอดีตก็สามารถบอกได้ครับว่า อดีตกับปัจจุบันมันตอนนี้มันไม่เหมือนกันนะ เพื่อให้เรารับมือกับอนาคตต่อไป

**สรุปได้รึยัง?**

ครับๆๆ ภาพรวมของ K-means นั้นก็คือการนำ Data ที่อยู่ในรูปแบบตัวเลขสถิตินำมาวิเคราะห์เพื่อหา Insight อะไรบางอย่าง ซึ่งก็ขึ้นอยู่กับความหมายภายใน Data นั้นๆครับว่ามีอะไรอยู่ข้างในหวังว่าบทความนี้จะเป็นประโยชน์กับผู้ที่สนใจทุกท่านและนำไปประยุกตร์ใช้ในองค์กร ของท่านได้ไม่มากก็น้อยครับผม ปล. ขอบคุณวิชาความรู้จากอาจารย์ที่ทำให้เกิดการต่อยอดโดยไม่รู้จบครับ _/\_

Reference

-   https://www.kaggle.com/yersever/500-person-gender-height-weight-bodymassindex


> [Sorce: ](https://www.softnix.co.th/2018/09/06/%E0%B8%A7%E0%B9%88%E0%B8%B2%E0%B8%94%E0%B9%89%E0%B8%A7%E0%B8%A2-k-means-%E0%B9%81%E0%B8%A5%E0%B8%B0%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B8%9B%E0%B8%A3%E0%B8%B0%E0%B8%A2%E0%B8%B8%E0%B8%81%E0%B8%95%E0%B8%A3/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0OTY4NjA1MDYsLTM2NDQyODIxNV19
-->