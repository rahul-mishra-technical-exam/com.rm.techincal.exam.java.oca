# String
---------------------------------------------------

```
        String s1 = "OCAJP";
        String s2 = "OCAJP" + "";
        System.out.println(s1 == s2);
```

* Please note that Strings computed by concatenation at compile time, will be referred by String Pool during execution. 
  Compile time String concatenation happens when both of the operands are compile time constants, 
  such as literal, final variable etc.

* For the statement, String s2 = "OCAJP" + "";, `"OCAJP" + ""` is a constant expression 
  as both the operands "OCAJP" and "" are String literals,
  which means the expression `"OCAJP" + ""` is computed at compile-time and results in String literal "OCAJP".

* So, during compilation, Java compiler translates the statement
  String s2 = "OCAJP" + ""; to String s2 = "OCAJP";
  As "OCAJP" is a String literal, hence at runtime it will be referred by String Pool.

* When Test class is executed,
  s1 refers to "OCAJP" (String Pool object).
  s2 also refers to same String pool object "OCAJP".
  s1 and s2 both refer to the same String object and that is why s1 == s2 returns true.

* For below code snippet:

    String s1 = "OCAJP";
    String s2 = s1 + "";
    System.out.println(s1 == s2);
    Output is false, as s1 is a variable and `s1 + ""` is not a constant expression, 
    therefore this expression is computed only at runtime and a new non-pool String object is created.

------------------------------------------------------------------------------------------------------------------------
```
         StringBuilder sb = new StringBuilder("Java");
         String s1 = sb.toString();
         String s2 = sb.toString();
```

* toString() method defined in StringBuilder class doesn't use String literal 
  rather uses the constructor of String class to create the instance of String class.

* So both s1 and s2 refer to different String instances even though their contents are same.
  s1 == s2 returns false.

------------------------------------------------------------------------------------------------------------------------
```
        StringBuilder sb = new StringBuilder();
        System.out.println(sb.append(null).length());
```

* 'append' method is overloaded in StringBuilder class: append(String), append(StringBuffer) and append(char[]) etc.
  
* In this case compiler gets confused as to which method `append(null)` 
  can be tagged because String, StringBuffer and char[] are not related to each other in multilevel inheritance.
  Hence `sb.append(null)` causes compilation error.
  
------------------------------------------------------------------------------------------------------------------------