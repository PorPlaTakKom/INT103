#  Polymorphism
> Polymorphism คือทำให้ object เปลี่ยนรูปได้

## ตัวอยย่าง

สมมุติว่าเราต้องเขียน โปรแกรมบัญชีธนาคาร เหมือนเดิมละกัน โดยมันมี บัญชีออมทรัพย์ กับ บัญชีกระแสรายวัน โดยมีโค้ดแบบง่ายๆไว้ประมาณนี้

**Class SavingAccount**
```
public class SavingAccount {
    protected double balance;
    public double Balance;
    public String OwnerName;

    public SavingAccount(String OwnName){
        this.OwnerName = OwnName;
        this.balance = 0;
    }

    public void Deposit(double amount){
        if( amount > 0){
            balance += amount;
        }
    }

    public double getBalance() {
        return balance;
    }

    public String getOwnerName() {
        return OwnerName;
    }

    public void setOwnerName(String ownerName) {
        OwnerName = ownerName;
    }
}

```
**Class CurrentAccount**
```
public class CurrentAccount {
    protected double balance;
    public double Balance;
    public String OwnerName;

    public CurrentAccount(String OwnName){
        this.OwnerName = OwnName;
        this.balance = 0;
    }

    public void Deposit(double amount){
        if( amount > 0){
            balance += amount;
        }
    }

    public double getBalance() {
        return balance;
    }

    public String getOwnerName() {
        return OwnerName;
    }

    public void setOwnerName(String ownerName) {
        OwnerName = ownerName;
    }
}
```

แล้วสมมุติว่าเราต้องเขียนให้มัน ถอนเงิน ให้กับบัญชีทั้ง 2 แบบนี้ได้ล่ะ เราจะเขียนยังไง?
ถ้าเอาแบบง่ายก่อน ก็สร้าง method ให้มันถอนเงินได้ใช่ป่ะ

มันก็ทำงานได้นะ แต่ลองคิดดูว่าถ้าเรามีบัญชีอีกหลายๆประเภทเข้ามาล่ะ? เราจะมี method พวกนี้กี่ตัว?

**วิเคราะห์ปัญหากันนิสนุง**

> ปัญหาที่เราเจออยู่ตอนนี้คือ object ที่เราสร้างขึ้นมา มันจะต้องใช้กับ data type ที่มันเป็นอยู่เท่านั้น มันเลยทำให้เราไม่สามารถส่ง object ของ SavingAccount ไปยัง CurrentAccount ได้ และทางตรงข้ามกันเราก็ส่ง object ของ CurrentAccount ไปยัง SaveingAccount ไม่ได้ด้วยเช่นกัน เพราะ object มันผูกกับ data type ที่มันเป็นอยู่นั่นเอง

**วิธีแก้ปัญหา**

> ตามหัวข้อคือเราจะใช้ Polymorphism มาแก้ปัญหาในรอบนี้ยังไงล่ะ ซึ่งการใช้ใช้ Polymorphism ได้เราจะต้องใช้หลักของ Inheritance เข้ามาช่วยด้วยดังนั้นก็แก้โค้ดให้มันเป็นแม่ลูกกันหน่อยนึง ตามตัวอย่างในเรื่อง Inheritance เลย

<p align="center">
  <img src="https://gblobscdn.gitbook.com/assets%2F-Lm0_idNbY6k1lwp6hm4%2F-M1lfqlFTvI3gmheTI_q%2F-M1lfv-2-JCTy1CgkFXy%2Fimage%20(952).png">
</p>

> ซึ่งหลักจากที่เราทำ Inheritance มาเรียบร้อย เราจะได้ความสามารถของ Polymorphism มาด้วย นั่นคือ
การเปลี่ยนรูปได้ นั่นหมายความว่า object นั้นๆมันจะไม่ได้ผูกติดกับ data type ที่มันอยู่แล้วนั่นเอง

ดังนั้นเราจะสามารถเขียนโค้ดแบบนี้ได้

```
BankAccount acc1 = new SavingAccount();
BankAccount acc2 = new CurrentAccount();
```

จะเห็นว่าตัว acc1 และ acc2 ทั้งคู่มันเป็นคลาส์ BankAccount แต่มันก็สามารถเก็บ object ที่ไม่ใช่ BankAccount ได้นั่นเอง ดังนั้นเราก็สามารถที่จะทำให้โค้ดของเรารองรับการทำงานของ บัญชีหลายๆรูปแบบในอนาคตได้แล้ว โดยการเขียนโค้ดเพียงแค่ตัวนี้เท่านั้น

## ตัวอยย่าง 2

ก่อนอื่นอยากให้เข้าใจตรงกันก่อนว่า โดยปรกติตัวแปรมันจะทำงานตามที่ type ที่มันเป็นอยู่เท่านั้น เช่น เรามีคลาส Dog กับ Cat

```
public class Dog { }
public class Cat { }
```
ถ้าเราจะไปสร้าง object ของคลาส Dog ออกมา เราก็ต้องใช้ตัวแปรที่เป็นคลาส Dog มาเก็บมันเท่านั้น
```
Dog d1 = new Dog();
```
ไม่สามารถสร้าง object ของคลาส Dog ไปเก็บไว้กับตัวแปรที่เป็นคลาส Cat ได้เลย
```
Cat c1 = new Dog(); // Error
```
นี่แหละคือสิ่งที่เรียกว่า object มันผูกกับ data type ที่มันเป็นอยู่ นั่นเอง

>การที่โปรแกรมของเราสามารถทำ Polymorphism ได้มันจะเป็นการ ปลดล๊อค การผูกกันที่ว่านี้ เลยทำให้โค้ดเรายืดหยุ่นขึ้น นำกลับมาใช้งานใหม่ได้ง่ายขึ้น โดยตัวหนึ่งที่เรานำมาทำให้เกิด Polymorphism ได้นั่นก็คือการทำ Inheritance นั่นเอง ดังนั้นเมื่อเราแก้โค้ดให้เป็นแบบนี้

```
public class Animal { }
public class Dog : Animal { }
public class Cat : Animal { }
```
มันเลยทำให้คลาส Dog และ Cat สามารถ เปลี่ยนรูป ตัวมันเองให้ตัวแปรที่เป็น Animal สามารถเก็บ object เหล่านั้นได้

```
Animal dog = new Dog();
Animal cat = new Cat();
```

**การเปลี่ยนรูป**\
จากตัวอย่างด้านบนคือการเปลี่ยนรูป จาก Dog หรือ Cat กลายเป็น Animal เลยทำให้ตัวแปร Animal สามารถทำงานร่วมกัน Dog และ Cat ได้นั่นเอง โดยมันมีกฏอยู่ว่า

> Base Class สามารถเก็บ Sub Class ได้ แต่ Sub Class ไม่ สามารถเก็บ Base Class ได้

นั่นหมายความว่า Animal สามารถเก็บ object ที่เป็น Sub Class ของมันได้นั่นคือ Dog และ Cat แต่เราไม่สามารถทำตรงข้ามกันได้ นั่นคือ Dog และ Cat ไม่สามารถเก็บ object ที่เป็น Animal ได้นั่นเอง

```
Dog dog = new Animal(); // Error
Cat cat = new Animal(); // Error
```

## Interface
อีกตัวอย่างหนึ่งในการทำ Polymorphism นั่นคือการใช้ Interface นั่นเอง เช่น เครื่องใช้ไฟฟ้าสามารถเปิด/ปิดได้ โดยมีทีวีและมือถือเป็นเครื่องใช้ไฟฟ้า

<p align="center">
  <img src="https://gblobscdn.gitbook.com/assets%2F-Lm0_idNbY6k1lwp6hm4%2F-M1lfqlFTvI3gmheTI_q%2F-LshewbPaTTiMoeQ6Nrm%2Fimage.png">
</p>

จากรูปเราก็สามารถทำ Polymorphism ได้เช่นกัน ตามนี้
```
class demo {

    public static void main(String[] args) {
        IElectronic e1 = new Television();
        e1.TunrOn();
        e1.TunrOff();
        System.out.println("-----------------------");
        IElectronic e2 = new Mobile();
        var mobile = (Mobile)e2;
        mobile.TunrOn();
        mobile.TunrOff();
    }

}

interface IElectronic {
    void TunrOn();
    void TunrOff();
}

class Television implements IElectronic {

    @Override
    public void TunrOn() {
        System.out.println("TrunOn Television");
    }

    @Override
    public void TunrOff() {
        System.out.println("TrunOFF Television");
    }
}

class Mobile implements IElectronic {

    @Override
    public void TunrOn() {
        System.out.println("TrunOn Mobile");
    }

    @Override
    public void TunrOff() {
        System.out.println("TrunOFF Mobile");
    }
}
```

> **ที่มาข้อมูล:** 
 www.saladpuk.com