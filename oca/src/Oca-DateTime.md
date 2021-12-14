# DATE AND TIME
-----------------------------------------------------------

>  LocalDate date = LocalDate.of(2020, 9, 31);

* LocalDate.of(...) method first validates year, then month and finally day of the month. 
* September can't have 31 days so LocalDate.of(...) method throws an instance of java.time.DateTimeException class

-------------------------------------------------------------

```
         LocalDate date = LocalDate.parse("1947-08-14");
         LocalTime time = LocalTime.MAX;
         System.out.println(date.atTime(time));
```

* LocalTime.MIN --> {00:00}, 
* LocalTime.MAX --> {23:59:59.999999999}, 
* LocalTime.MIDNIGHT --> {00:00}, 
* LocalTime.NOON --> {12:00}. 

* date.atTime(LocalTime) method creates a LocalDateTime instance by combining date and time parts.

* toString() method of LocalDateTime class prints the date and time parts separated by T in upper case

------------------------------------------------------------------------------------------------------------------------

```
         LocalDate date = LocalDate.of(2012, 1, 11);
         Period period = Period.ofMonths(2);
         DateTimeFormatter formatter = DateTimeFormatter.ofPattern("MM-dd-yy");
         System.out.print(formatter.format(date.minus(period)));
```

* date --> {2012-01-11}, period --> {P2M}, date.minus(period) --> {2011-11-11}
  [subtract 2 months period from {2012-01-11}, month is changed to 11 and year is changed to 2011].
  
* formatter -> {MM-dd-yy}, when date {2011-11-11} is formatter in this format 11-11-11 is printed on to the console

------------------------------------------------------------------------------------------------------------------------










