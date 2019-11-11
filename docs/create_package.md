# การสร้าง Package ควบคุมมอเตอร์ ด้วย Roboteq

## ขั้นตอนการสร้าง Package  ด้วย Catkin_create
1.หากคุณต้องการ สร้าง __Paackage__ ให้เปิด __Teminal__ `ctrl+alt+T`แล้วพิมพ์คำสั่ง ไปยัง Repository ของ src ใน project workspace
```s
cd ~/catkin_ws/src
```
2.คำสั่งใช้สำหรับ Create package คือ `<catkin_create> <ตั้งชื่อ Package> [depend1] [depend2] [depend3]` โดย depend คือ การระบุหรืออ้างอิงไลบาร์ที่ต้องการใช้ภายใน Package
```
catkin_create_pkg roboteq ropy geometry__msgs tf nav_msgs
```
3.catkin จะสร้าง Package ที่ภายในประกอบด้วย 
```s
my_package/
  src 
  CMakeLists.txt
  package.xml 
```
4.เปิดเข้าไปใน src ภายใน package: roboteq แล้วสร้างไพล์ที่มีชื่อว่า roboteq.py
```
cd roboteq/src
touch roboteq.py
gedit roboteq.py
```
5.คัดลอกโปรแกรมด้านล่าง ลงใน _roboteq.py_ แล้ว __seave__ โปรแกรม
```python
#!/usr/bin/env python
import rospy
import serial
import time

ser = serial.Serial(
    port='/dev/ttyACM0',
    baudrate=115200,
    parity=serial.PARITY_ODD,
    stopbits=serial.STOPBITS_TWO,
    bytesize=serial.SEVENBITS)
ser.isOpen()

def run():
    rospy.init_node('ohm_roboteq', anonymous=True)
    rate = rospy.Rate(10) # 10hz
    
    while not rospy.is_shutdown():

	    ser.write('!G 2 1000\r')
	    rospy.loginfo(' Send_data : !G 2 1000')
        rate.sleep()
        
if __name__ == '__main__':
    try:
        run()
    except rospy.ROSInterruptException:
        pass

```
6.ให้อนุญาติ file.py ทุกครั้งที่มีการสร้างขึ้นมาใหม่ เพียงครั้งเดียว โดยมีคำสั่งด้านล่าง
```
sudo chmod +x roboteq.py
```
7.เชื่อมต่อบอร์ด Roboteq กับเครื่องคอมพิวเตอร์แล้วตรวจสอบว่าเครื่องคอมพิวเตอร์ พบพอร์ตดังกล่าวหรือไม่
```s
ls -l /dev/ttyACM0

```
> ให้พิมพ์คำสั่งอนุญาติรับส่งผ่านพอร์ด แล้วตรวจสอบอีกครั้ง
```s
sudo chmod 666 /dev/ttyACM0
ls -l /dev/ttyACM0

```
8.ใช้คำสั่ง catkin_make ที่ project workspace แล้วเปิดโปรแกรม ___roscore__
```s
cd ~/catkin_ws/
catkin_make
roscore

```
9.ให้เปิด __Teminal__ `ctrl+alt+T`แล้วพิมพ์คำสั่งทดสอบโปรแกรมโดย 
```

rosrun roboteq robotqe.py

```

