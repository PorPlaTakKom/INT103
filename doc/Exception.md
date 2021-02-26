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

## ประเภทของ Execption

>1. แบบไม่ต้องตรวจสอบ: ส่วนมากมักเป็น RuntimeException โปรแกรมจะไม่บังคับตรวจ Exception เพราะต้อง RUN ถึงจะรู้

>2. แบบบังคับว่าต้องตรวจสอบ: เป็นกับการทำงาน อะไรซักอย่างนอกโปรแกรม เช่น การต่อ DataBase

## คำสั่งในการดักจับ Eexeption

try catch

```
public static void main(String[] args) {
        int[] x = {0,1,2};
        System.out.println("Start!!");
        try{
            for (int i = 0; i < 10; i++) {
                System.out.println("try" + x[i]);
            }
        }catch(ArrayIndexOutOfBoundsException aooe){
            System.out.println("catch-Array");
        }catch(Exception e){
            System.out.println("catch-Exception");
        }finally{
            System.out.println("End!!");
        }
   }
```

throw
```
public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int[] x = {0,1,2};
        System.out.println("Start!!");
        try{
            System.out.print("Enter Number of Array: ");
            int a = sc.nextInt();
            if(a > x.length-1) throw new ArrayIndexOutOfBoundsException("Error");
            System.out.println(x[a]);
        }catch(ArrayIndexOutOfBoundsException e){
            e.printStackTrace();
        }
   }
```

throws
```
 public static void main(String[] args) {
        System.out.println("Start!!");
        try{
            demo();
        }catch(Exception e){
            e.printStackTrace();
        }
   }
    public static void demo() throws Exception {
        int x = Integer.parseInt("Hello");
    }
```