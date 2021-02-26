# Exception

>คือ สิ่งที่ผิดพลาด อะไรสักอย่างที่เกิดขึ้นเวลา Run โปรแกรม ( ไม่ใช่ Bug )

***ตัวอย่าง***
```
public static void main(String[] args) {
        int x = Integer.parseInt("Hello");
}
```
ทำการเปลี่ยน DataType String เป็น Integer ตามโค้ด ตัวโปรแกรมจะสามารถ Compile ผ่าน แต่ถ้าเรารัน

***สิ่งที่ได้***
```
Exception in thread "main" java.lang.NumberFormatException: For input string: "Hello"
```
มันฟ้องว่าไม่สามารถเปลี่ยนได้เพราะ Hello มันเป็นเป็นตัวเลขไม่ได้


***มาดูกัน JAVA มี Exception อะไรบ้าง***
<p align="center">
  <img src="https://i.imgur.com/7v6BEy0.png">
</p>
