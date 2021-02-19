# Inheritance

> Inheritance คือการสืบทอดคุณสมบัติ จาก Model A ไปยัง Model อื่นๆได้ ซึ่งมันจะช่วยให้เราเพิ่มความสามารถใหม่ๆเข้าไปได้โดยที่ไม่ต้องไปยุ่งกับโค้ดเก่าที่เคยเขียนไว้
***
## ตัวอยย่าง

> สมมุติว่าเราต้องเขียน โปรแกรมบัญชีธนาคาร ซึ่งบัญชีออมทรัพย์สามารถเก็บข้อมูล เงินในบัญชี และ เจ้าของบัญชี ได้ และอย่าลืมนะว่าเราต้อง ฝากเงินเข้าบัญชี ได้ด้วย ดังนั้นเราก็น่าจะได้ Model ออกมาประมาณนี้

***
**Class SavingAccount**
```
public class SavingAccount {
    private double balance;
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
    private double balance;
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
> เราจะเห็นว่าโค้ด บัญชีออมทรัพย์ และ บัญชีกระแสรายวัน มันเหมือนกันเลย! ซึ่งถามว่าผิดไหม คำตอบคือไม่ผิดครับ แต่ถ้าเราปล่อยมันไว้แบบนี้เราจะมีปัญหาในอนาคต เช่น เรามาพบทีหลังว่าโค้ดมันเขียนผิดนะ แต่เราก็ copy ไปวางไว้ที่อื่นเรียบร้อยแล้ว
***

## การใช้ Inheritance แก้ปัญหา

>เราสามารถนำหลักการ Inheritance มาช่วยในเรื่องนี้ได้ โดยการสร้าง Model ต้นแบบ ขึ้นมา แล้วทำการย้ายของที่ซ้ำกันไปไว้ในตัวต้นแบบตัวนั้น ซึ่งในตัวอย่างของที่เรากำลังทำอยู่มันคือ บัญชีธนาคาร ดังนั้นเราเลยสร้างคลาส BankAccount ขึ้นมาใหม่

**Class BankAccount**
```
public class BankAccount {
    private double balance;
    public double Balance;
    public String OwnerName;

    public BankAccount(String OwnName){
        this.OwnerName = OwnName;
        this.balance = 0;
    }

    public void Deposit(double amount){
        if( amount > 0){
            balance += amount;
        }
    }

    public double getBalance() { return balance; }

    public String getOwnerName() { return OwnerName; }

    public void setOwnerName(String ownerName) { OwnerName = ownerName; }
}

```
> แล้วทำการย้ายของที่มันซ้ำกันจาก บัญชีออมทรัพย์ กับ บัญชีกระแสรายวัน มาไว้ในตัว BankAccount แล้วนำเอาไป สืบทอด

**Class SavingAccount**
```
public class SavingAccount extends BankAccount {
    public SavingAccount(String OwnName){
        super(OwnName);
    }
}
```
**Class CurrentAccount**
```
public class CurrentAccount extends BankAccount {
    public CurrentAccount(String OwnName){
        super(OwnName);
    }
}
```
>เพียงเท่านี้ บัญชีออมทรัพย์ และ บัญชีกระแสรายวัน ก็จะมีความสามารถทุกอย่างที่ตัวต้นแบบมีนั่นเอง ดังนั้นลองเขียนโค้ดเล่นกับบัญชีทั้ง 2 ตัวของเราดู