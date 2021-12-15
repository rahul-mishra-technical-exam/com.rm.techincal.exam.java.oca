# Condition
-----------------------------------------------------------

```
    public static void main(String[] args) {
         double price = 90000;
         String model;
         if(price > 100000) {
             model = "Tesla Model X";
         } else if(price <= 100000) {
             model = "Tesla Model S";
         }
           System.out.println(model);
     }
```

* In this case "if - else if" block is used and not "if - else" block.

* 90000 is assigned to variable 'price' but you can assign parameter value or call some method returning double value, such as:
  'double price = currentTemp();'.

* In these cases compiler will not know the exact value until runtime, hence Java Compiler is not sure which boolean expression will be evaluated to true and so variable model may not be initialized.

* Usage of LOCAL variable, 'model' without initialization gives compilation error. Hence, System.out.println(model); gives compilation error.