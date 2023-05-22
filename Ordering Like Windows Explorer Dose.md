### Order Mysql Like Windows Explorer 
I think this source code i made is not perfect, but it's the simplest and the clostes with the case that one i want to solve :)
So if you just order by name with asc order your order number will be [1, 10, 11, 12, .., 19, 2, 20] but with this code you can make them to be [1, 2, 3, ... ,9 , 10, 11] until the end
But the limitation of this code is i just try that to the table that i make bellow, so if you have more crazy case i would love it if you can share the case wit me :D.

### Code For Order
```
SELECT * FROM employees
ORDER BY CAST(SUBSTRING(name, 9) AS UNSIGNED), NAME asc;
```

### Create Table
# The source code bellow will random the order so you can ensure if the order is correct or not :)
```
CREATE TABLE employees (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(100)
);

INSERT INTO employees (name)
SELECT tmp.name FROM (
    SELECT 'employee 1 - age 30' AS NAME UNION
    SELECT 'employee 2 - age 29' UNION
    SELECT 'employee 3 - age 28' UNION
    SELECT 'employee 4 - age 27' UNION
    SELECT 'employee 5 - age 26' UNION
    SELECT 'employee 6 - age 25' UNION
    SELECT 'employee 7 - age 24' UNION
    SELECT 'employee 8 - age 23' UNION
    SELECT 'employee 9 - age 22' UNION
    SELECT 'employee 10 - age 21' UNION
    SELECT 'employee 11 - age 20' UNION
    SELECT 'employee 12 - age 19' UNION
    SELECT 'employee 13 - age 18' UNION
    SELECT 'employee 14 - age 17' UNION
    SELECT 'employee 15 - age 16' UNION
    SELECT 'employee 16 - age 15' UNION
    SELECT 'employee 17 - age 14' UNION
    SELECT 'employee 18 - age 13' UNION
    SELECT 'employee 19 - age 12' UNION
    SELECT 'employee 20 - age 11' UNION
    SELECT 'employee 21 - age 10' UNION
    SELECT 'employee 22 - age 9' UNION
    SELECT 'employee 23 - age 8' UNION
    SELECT 'employee 24 - age 7' UNION
    SELECT 'employee 25 - age 6' UNION
    SELECT 'employee 26 - age 5' UNION
    SELECT 'employee 27 - age 4' UNION
    SELECT 'employee 28 - age 3' UNION
    SELECT 'employee 29 - age 2' UNION
    SELECT 'employee 30 - age 1' UNION
    SELECT 'employee 1' UNION
    SELECT 'employee 2' UNION
    SELECT 'employee 3' UNION
    SELECT 'employee 4' UNION
    SELECT 'employee 5' UNION
    SELECT 'employee 6' UNION
    SELECT 'employee 7' UNION
    SELECT 'employee 8' UNION
    SELECT 'employee 9' UNION
    SELECT 'employee 10' UNION
    SELECT 'employee 11' UNION
    SELECT 'employee 12' UNION
    SELECT 'employee 13' UNION
    SELECT 'employee 14' UNION
    SELECT 'employee 15' UNION
    SELECT 'employee 16' UNION
    SELECT 'employee 17' UNION
    SELECT 'employee 18' UNION
    SELECT 'employee 19' UNION
    SELECT 'employee 20' UNION
    SELECT 'employee 21' UNION
    SELECT 'employee 22' UNION
    SELECT 'employee 23' UNION
    SELECT 'employee 24' UNION
    SELECT 'employee 25' UNION
    SELECT 'employee 26' UNION
    SELECT 'employee 27' UNION
    SELECT 'employee 28' UNION
    SELECT 'employee 29' UNION
    SELECT 'employee 30'
) AS tmp
ORDER BY RAND();
```

### Reset Table
In the name of experience you will make some mistake some day XD
```
TRUNCATE TABLE employees;
```
