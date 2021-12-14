# Collection
-----------------------------------------------------------
> List addition
```
         List<String> list1 = new ArrayList<>();
         list1.add("A");
         list1.add("D");
 
         List<String> list2 = new ArrayList<>();
         list2.add("B");
         list2.add("C");
```

* list1 --> [A, D], 

* list2 --> [B, C], 

* list1.addAll(1, list2); is almost equal to list1.add(1, [B, C]); => Inserts B at index 1, C takes index 2 and D is moved to index 3. list1 --> [A, B, C, D]
---------------------------------------------------------

```
         ArrayList<Counter> original = new ArrayList<>();
         original.add(new Counter(10));
 
         ArrayList<Counter> cloned = (ArrayList<Counter>) original.clone();
         cloned.get(0).count = 5;
```

* Let's see what is happening during execution

 ![](.Oca-Collection_images/ArrayListCloned.png)
  
*  main(String [] args) method goes on to the top of the STACK.
  
  1. ArrayList<Counter> original = new ArrayList<>(); =>
     It creates an ArrayList object [suppose at memory location 15EE00] and variable 'original' refers to it.
  
  2. original.add(new Counter(10)); => 
     It creates a Counter object [suppose at memory location 25AF06] and adds it as a first element of the ArrayList.
     This means element at 0th index of the ArrayList instance refers to Counter object at the memory location 25AF06.
  
  3. ArrayList<Counter> cloned = (ArrayList<Counter>) original.clone(); => original.clone() creates a new array list object,
     [suppose at memory location 45BA12] and then it will copy the contents of the ArrayList object stored at [15EE00].
     So, cloned contains memory address of the same Counter object.
     In this case, original != cloned, but original.get(0) == cloned.get(0). 
     This means both the array lists are created at different memory location but refer to same Counter object. 
  
  4. cloned.get(0).count = 5; => cloned.get(0) returns the Counter object stored at the memory location 25AF06 and .count = 5 
     means change the value of count variable of the Counter object (stored at memory location 25AF06) to 5. 
  
  5. System.out.println(original); Prints the element of ArrayList original, which is: {25AF06} and toString() method prints:
     [Counter-5] as Counter object referred by [25AF06] is [Counter object (5)].

-----------------------------------------------------------------------------------
> remove method is overloaded: remove(int) and remove(Object). 

```
List<Character> list = new ArrayList<>();
         list.add(0, 'V');
         list.add('T');
         list.add(1, 'E');
         list.add(3, 'O');
 
         if(list.contains('O')) {
             list.remove('O');
         }
```

* list.add(0, 'V'); => char 'V' is converted to Character object and stored as the first element in the list. list --> [V]. 

* list.add('T'); => char 'T' is auto-boxed to Character object and stored at the end of the list. list --> [V,T]. 

* list.add(1, 'E'); => char 'E' is auto-boxed to Character object and inserted at index 1 of the list, 
  this shifts T to the right. list --> [V,E,T]. 
  
* list.add(3, 'O'); => char 'O' is auto-boxed to Character object and added at index 3 of the list. list --> [V,E,T,O].

* list.contains('O') => char 'O' is auto-boxed to Character object and as Character class overrides equals(String) method this expression returns true. Control goes inside if-block and executes: list.remove('O');.

* char can be easily assigned to int so compiler tags remove(int) method.
  list.remove(<ASCCI value of 'O'>);
  ASCCI value of 'A' is 65 (this everybody knows) so ASCII value of 'O' will be more than 65.

* list.remove('O') throws runtime exception, as it tries to remove an item from the index greater than 65
   but allowed index is 0 to 3 only.