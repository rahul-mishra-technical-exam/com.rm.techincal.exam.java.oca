# Array
-----------------------------------------------------------

```
        String [] arr = {"I", "N", "S", "E", "R", "T"};
        for(/*INSERT*/) {
            if (n % 2 == 0) {
                continue;
            }
            System.out.print(arr[n]); //Line n1
        }
    }
}


And below options:

1. int n = 0; n < arr.length; n += 1

2. int n = 0; n <= arr.length; n += 1

3. int n = 1; n < arr.length; n += 2

4. int n = 1; n <= arr.length; n += 2
```

* Also note that, for values of n = 0, 2, 4, 6; Line n1 would not be executed, which means even if the value of n is 6, above code will not throw ArrayIndexOutOfBoundsException.

* For 1st option [int n = 0; n < arr.length; n += 1], values of n used: 0, 1, 2, 3, 4, 5 and because of continue; statement, Line n1 will not execute for 0, 2 & 4 and it will execute only for 1, 3 & 5 and therefore NET will be printed.

* For 2nd option [int n = 0; n <= arr.length; n += 1], values of n used: 0, 1, 2, 3, 4, 5, 6 and because of continue; statement, Line n1 will not execute for 0, 2, 4 & 6 and it will execute only for 1, 3 & 5 and therefore NET will be printed.

* For 3rd option [int n = 1; n < arr.length; n += 2], values of n used: 1, 3, 5 and therefore NET will be printed.

* For 4th option [int n = 1; n <= arr.length; n += 2], values of n used: 1, 3, 5 and therefore NET will be printed.

------------------------------------------------------------

```
     public static void main(String[] args) {
         short [] args = new short[]{50, 50};
         args[0] = 5;
         args[1] = 10;
         System.out.println("[" + args[0] + ", " + args[1] + "]");
     }
```

* main method's parameter variable name is "args" and it is a local to main method.

* So, same name "args" can't be used directly within the curly brackets of main method.

* short [] args = new short[]{50, 50}; gives compilation error for using same name for local variable.

