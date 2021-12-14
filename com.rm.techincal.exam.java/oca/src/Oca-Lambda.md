# LAMBDA
-----------------------------------------------------------

```(Employee e) -> { return e.getSalary() >= 10000; }, ```

* Can be simplified to:  (e) -> { return e.getSalary() >= 10000; } => type can be removed from left side of the expression. 

* Further simplified to: e -> { return e.getSalary() >= 10000; } => if there is only one parameter in left part, 
  then round brackets (parenthesis) can be removed. 

* Further simplified to: e -> e.getSalary() >= 10000 => if there is only one statement in the right side 
  then semicolon inside the body, curly brackets and return statement can be removed. 
  But all 3 [return, {}, ;] must be removed together.

* NOTE: there should not be any space between - and > of arrow operator.

-----------------------------------------------------------