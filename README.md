# Содержание SQL-ex
+ [1](#1)
+ [2](#2)
+ [3](#3)
+ [4](#4)
+ [5](#5)
+ [6](#6)
+ [7](#7)
+ [8](#8)
+ [9](#9)
+ [10](#10)
+ [11](#11)
+ [12](#12)
+ [13](#13)
+ [14](#14)
+ [15](#15)
+ [16](#16)
+ [17](#17)
+ [18](#18)
+ [19](#19)
+ [20](#20)
+ [21](#21)
+ [22](#22)
+ [23](#23)
+ [24](#24)
+ [25](#25)




# Задачи и решения 

## 1

https://sql-ex.ru/learn_exercises.php?LN=1

```sql
SELECT model, speed, hd
FROM PC
WHERE price < 500
```
## 2

https://sql-ex.ru/learn_exercises.php?LN=2

```sql
SELECT DISTINCT maker
FROM Product 
WHERE type='Printer';
```
## 3

https://sql-ex.ru/learn_exercises.php?LN=3

```sql
SELECT model, ram, screen 
FROM laptop
WHERE price > 1000;
```
## 4

https://sql-ex.ru/learn_exercises.php?LN=4

```sql
 SELECT * 
 FROM printer 
 WHERE color = 'y';
```
## 5

https://sql-ex.ru/learn_exercises.php?LN=5

```sql
SELECT model ,speed , hd  
FROM pc 
WHERE (cd = '12x' or cd = '24x') AND price < 600
```

## 6

https://sql-ex.ru/learn_exercises.php?LN=6

```sql
SELECT maker, speed  
FROM Product inner join Laptop on Product.model = Laptop.model   
WHERE hd >= 10
```
## 7

https://sql-ex.ru/learn_exercises.php?LN=7

```sql
SELECT laptop.model , laptop.price  
FROM laptop 
INNER JOIN product ON laptop.model = product.model  
WHERE product.maker= 'B' 
UNION 
SELECT pc.model , pc.price 
FROM pc 
INNER JOIN product on pc.model = product.model  
WHERE product.maker= 'B' 
UNION 
SELECT printer.model , printer.price 
FROM printer 
INNER JOIN product ON printer.model = product.model  
WHERE product.maker= 'B'
```
## 8

https://sql-ex.ru/learn_exercises.php?LN=8

```sql
SELECT maker 
FROM product 
WHERE type='PC' AND maker not in (SELECT maker FROM product WHERE type = 'Laptop') 
GROUP BY maker
```

## 9

https://sql-ex.ru/learn_exercises.php?LN=9

```sql
SELECT maker 
FROM pc 
INNER JOIN product ON pc.model = product.model 
WHERE speed >= 450 
GROUP BY maker
```

## 10

https://sql-ex.ru/learn_exercises.php?LN=10

```sql
SELECT model, price  
FROM printer 
WHERE price = (SELECT max(price) FROM printer)
```
## 11

https://sql-ex.ru/learn_exercises.php?LN=11

```sql
SELECT avg(speed) 
FROM pc
```

## 12

https://sql-ex.ru/learn_exercises.php?LN=12

```sql
SELECT avg(speed) 
FROM laptop 
WHERE price > 1000 
```
## 13

https://sql-ex.ru/learn_exercises.php?LN=13

```sql
SELECT avg(speed) 
FROM pc 
INNER JOIN product ON pc.model= product.model 
WHERE maker = 'A'   
GROUP BY maker 
```

## 14

https://sql-ex.ru/learn_exercises.php?LN=14

```sql
SELECT s.class, s.name, c.country
FROM ships s
LEFT JOIN classes c ON s.class = c.class
WHERE c.numguns >= 10
```
## 15

https://sql-ex.ru/learn_exercises.php?LN=15

```sql
SELECT hd  
FROM pc 
GROUP BY hd having count(model)>1 
```
## 16

https://sql-ex.ru/learn_exercises.php?LN=16

```sql
SELECT DISTINCT B.model AS model, A.model AS model, A.speed, A.ram 
FROM PC AS A, PC B 
WHERE A.speed = B.speed AND A.ram = B.ram AND A.model < B.model 
```
## 17

https://sql-ex.ru/learn_exercises.php?LN=17

```sql
SELECT distinct type,laptop.model,speed
FROM laptop 
INNER JOIN product ON laptop.model= product.model  
WHERE speed < (select MIN(speed) FROM pc) 
```
## 18

https://sql-ex.ru/learn_exercises.php?LN=18

```sql
SELECT DISTINCT maker,price 
FROM printer 
INNER JOIN product ON printer.model= product.model  
WHERE price = (SELECT min(price)FROM printer WHERE color = 'y' ) AND color = 'y'  
```
## 19

https://sql-ex.ru/learn_exercises.php?LN=19

```sql
SELECT maker ,avg(screen)as Avg_screen 
FROM laptop 
INNER JOIN product ON laptop.model =  product.model 
GROUP BY maker  
```
## 20

https://sql-ex.ru/learn_exercises.php?LN=20

```sql
SELECT maker, count(model) as Count_Model 
FROM product 
WHERE type = 'pc' 
GROUP BY maker having count(model) >= 3;
```
