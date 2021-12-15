# OOP
-----------------------------------------------------------
```
class Message {
    String msg = "Happy New Year!";
    
    public void print() {
        System.out.println(msg);
    }
}
 
public class Test {
    public static void change(Message m) { //Line n5
        m = new Message(); //Line n6
        m.msg = "Happy Holidays!"; //Line n7
    }
    
    public static void main(String[] args) {
        Message obj = new Message(); //Line n1
        obj.print(); //Line n2
        change(obj); //Line n3
        obj.print(); //Line n4
    }
}
```

* It is pass-by-reference scheme.Initially, msg = "Happy New Year!"

* Call to method change(Message) doesn't modify the msg property of passed object rather it creates another Message object and modifies the msg property of new object to "Happy Holidays!"

* So, the instance of Message referred by obj remains unchanged.

* Hence in the output, you get: Happy New Year! Happy New Year!

-------------------------------------------------------------
```
public class A {
     public void print() {
         System.out.println("A");
     }
}


//B.java
package com.udayan.oca;
 
public class B extends A {
     public void print() {
         System.out.println("B");
     }
}


//Test.java
package com.udayan.oca.test;
 
import com.udayan.oca.*;
 
public class Test {
     public static void main(String[] args) {
         A obj1 = new A();
         B obj2 = (B)obj1;
         obj2.print();
     }
}
```

* Class A and B are declared public and inside same package com.udayan.oca. 
  Method print() of class A has correctly been overridden by B.

* print() method is public so no issues in accessing it anywhere.

* A obj1 = new A(); => obj1 refers to an instance of class A.

* B obj2 = (B)obj1; => obj1 is of type A and it is assigned to obj2 (B type), 
  hence explicit casting is necessary. obj1 refers to an instance of class A, 
  so at runtime obj2 will also refer to an instance of class A.
  sub type can't refer to an object of super type so at runtime B obj2 = (B)obj1; will throw ClassCastException.
  
----------------------------------------------------------------------------------------------------------------------

```
interface Printable {
     public void setMargin();
     public void setOrientation();
}
 
abstract class Paper implements Printable { //Line 7
     public void setMargin() {}
     //Line 9
}
 
class NewsPaper extends Paper { //Line 12
     public void setMargin() {}
     //Line 14
}
```

* First you should find out the reason for compilation error.
  Methods declared in Printable interface are implicitly abstract, no issues with Printable interface.

* class Paper is declared abstract and it implements Printable interface, 
  it overrides setMargin() method but setOrientation() method is still abstract.
  No issues with class Paper as it is an abstract class and can have 0 or more abstract methods. 

* class NewsPaper is concrete class and it extends Paper class (which is abstract).
  So class NewsPaper must override setOrientation() method OR it must be declared abstract.

* Replacing Line 9 with 'public abstract void setOrientation();' is not necessary and
  it will not resolve the compilation error in NewsPaper class.

* Replacing Line 7 with 'class Paper implements Printable {' will cause compilation failure of Paper
  class as it inherits abstract method 'setOrientation'.
  
------------------------------------------------------------------------------------------------------------------------

```
public class A {
     public int i1 = 1;
     protected int i2 = 2;
}


//B.java
package com.udayan.oca.test;
 
import com.udayan.oca.A;
 
public class B extends A {
     public void print() {
         A obj = new A();
         System.out.println(obj.i1); //Line 8
         System.out.println(obj.i2); //Line 9
         System.out.println(this.i2); //Line 10
         System.out.println(super.i2); //Line 11
     }
 
     public static void main(String [] args) {
         new B().print();
     }
```

* class A is declared public and defined in com.udayan.oca package, 
   there is no problem in accessing class A outside com.udayan.oca package.

*  class B is defined in com.udayan.oca.test package, to extend from class A either use import statement 
   "import com.udayan.oca.A;" or fully qualified name of the class com.udayan.oca.A. 
    No issues with this class definition as well.

*  Variable i1 is declared public in class A, so Line 8 doesn't cause any compilation error.
    Variable i2 is declared protected so it can only be accessed in subclass using inheritance 
    but not using object reference variable. obj.i2 causes compilation failure.

*  class B inherits variable i2 from class A, so inside class B it can be accessed by using either this or super.
   Line 10 and Line 11 don't cause any compilation error.