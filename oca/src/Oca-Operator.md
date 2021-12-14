# Operator

> If an expression has multiple ternary operators then number of ? and : should match

------------------------------------------------------------------
> System.out.println("Output is: " + 10 != 5);

* Binary plus (+) has got higher precedence than != operator.

* "Output is: " + 10 != 5 

* ("Output is: " + 10) != 5 

* [!= is binary operator, so we have to evaluate the left side first. + operator behaves as concatenation operator.] 

* "Output is: 10" != 5 

* Left side of above expression is String, and right side is int.

* But String can't be compared to int, hence compilation error
------------------------------------------------------------------
> Following are allowed in boolean expression of if statement:
  
  1. Any expression whose result is either true or false. e.g. age > 20 
  
  2. A boolean variable. e.g. flag 
  
  3. A boolean literal: true or false 
  
  4. A boolean assignment. e.g. flag = true
------------------------------------------------------------------
> System.out.println(-a++);

* First add parenthesis (round brackets) to the given expression: -a++.

* There are 2 operators involved. unary minus and Postfix operator. 

* -a++; [a = 100]. 

* -(a++); [a = 100] Postfix operator has got higher precedence than unary operator.   

* -(100); [a = 101] Use the value of a (100) in the expression and after that increase the value of a to 101. 

* -100; [a = 101] -100 is printed on to the console
------------------------------------------------------------------
> case values must evaluate to the same type / compatible type as the switch expression can use. 
  switch expression can accept following: 
  
*   char or Character 
  
*   byte or Byte 
  
*   short or Short 
  
*   int or Integer 
  
*   An enum only from Java 6 
  
*   A String expression only from Java 7

* In this case, switch expression [switch (var)] is of byte type.
  byte range is from -128 to 127.
  But in case expression [case 200], 
  200 is outside byte range and hence compilation error
  
------------------------------------------------------------------
> "Lucky no. 7" on to the console
```public class Test {
        public static void main(String[] args) {
            /*INSERT*/
            switch(var) {
                case 7:
                    System.out.println("Lucky no. 7");
                    break;
                default:
                    System.out.println("DEFAULT");
            }
        }
   }
```
* switch can accept primitive types: byte, short, int, char; wrapper types: Byte, Short, Integer, Character; String and enums.

* In this case, all are valid values but only 3 executes "case 7:". case is comparing integer value 7.

* NOTE: character seven, '7' is different from integer value seven, 7. So "char var = '7';" and "Character var = '7';" will print DEFAULT on to the console
------------------------------------------------------------------

> No break statement inside default, hence control enters in fall-through and executes remaining blocks until the break; is found or switch block ends.
  
```public class Test {
        public static void main(String[] args) {
            String fruit = "mango";
            switch (fruit) {
                default:
                    System.out.println("ANY FRUIT WILL DO");
                case "Apple":
                    System.out.println("APPLE");
                case "Mango":
                    System.out.println("MANGO");
                case "Banana":
                    System.out.println("BANANA");
                    break;
            }
        }
   }
```
 * So in this case, it prints APPLE, MANGO, BANANA one after another and break; statement takes control out of switch block. main method ends and program terminates successfully
 
------------------------------------------------------------------