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
+ [26](#26)
+ [27](#27)
+ [28](#28)
+ [29](#29)
+ [30](#30)
+ [31](#31)
+ [32](#32)
+ [33](#33)
+ [34](#34)
+ [35](#35)
+ [36](#36)
+ [37](#37)
+ [38](#38)
+ [39](#39)
+ [40](#40)
+ [41](#40)
+ [42](#42)
+ [43](#43)
+ [44](#44)
+ [45](#45)
+ [46](#46)
+ [47](#47)
+ [48](#48)
+ [49](#49)
+ [50](#50)


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
SELECT DISTINCT p.maker, l.speed
FROM laptop l
JOIN product p ON p.model = l.model
WHERE l.hd >= 10
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
## 21 

https://sql-ex.ru/learn_exercises.php?LN=21

```sql
SELECT maker , max(price) as Max_price 
FROM pc 
INNER JOIN product ON pc.model= product.model  
GROUP BY maker
```
## 22

https://sql-ex.ru/learn_exercises.php?LN=22

```sql
 SELECT speed, avg(price) 
 FROM pc 
 WHERE speed > '600' 
 GROUP by speed
```
## 23

https://sql-ex.ru/learn_exercises.php?LN=23

```sql
SELECT p.maker 
FROM product p 
JOIM pc pc ON p.model = pc.model 
WHERE pc.speed >= '750' intersect 
SELECT p.maker 
FROM product p 
JOIN laptop l ON p.model = l.model 
WHERE l.speed >= '750'
```

## 24

https://sql-ex.ru/learn_exercises.php?LN=24

```sql
WITH all_model AS (
SELECT model, price FROM pc
UNION ALL
SELECT model, price FROM printer
UNION ALL
SELECT model, price FROM laptop )
SELECT distinct model
FROM all_model WHERE price = ALL ( SELECT max(price) FROM all_model)
```

## 25

https://sql-ex.ru/learn_exercises.php?LN=25

```sql
SELECT distinct product.maker FROM product WHERE product.type='Printer'  
INTERSECT 
SELECT distinct product.maker FROM product INNER JOIN pc ON pc.model=product.model  
WHERE product.type='PC' AND pc.ram=(SELECT MIN(ram) FROM pc)  
AND pc.speed = (SELECT MAX(speed) FROM (SELECT distinct speed FROM pc 
WHERE pc.ram=(SELECT MIN(ram) FROM pc)) as t)
```
## 26

https://sql-ex.ru/learn_exercises.php?LN=26

```sql
SELECT t1.c/t1.d 
FROM( SELECT SUM(t.a) as c, SUM(t.b) as d 
FROM(  
SELECT SUM(pc.price) as a, COUNT(pc.code) as b FROM pc 
INNER JOIN product ON pc.model=product.model WHERE product.maker='A'  
UNION 
SELECT SUM(laptop.price) as a, COUNT(laptop.code) as b FROM laptop 
INNER JOIN product ON laptop.model=product.model WHERE product.maker='A') as t) as t1  
```
## 27

https://sql-ex.ru/learn_exercises.php?LN=27

```sql
SELECT maker,avg(hd)  
FROM product 
INNER JOIN pc ON product.model=pc.model   
WHERE maker in(select maker  from product  where type='printer')  
GROUP BY maker  
```
## 28

https://sql-ex.ru/learn_exercises.php?LN=28

```sql
SELECT count(maker) as qty 
FROM (SELECT distinct maker
FROM product 
GROUP BY maker having count(model) = 1) AS prod
```
## 29

https://sql-ex.ru/learn_exercises.php?LN=29

```sql
SELECT i.point, i.date, inc, out 
FROM income_o i 
LEFT JOIN outcome_o o on i.point = o.point and i.date = o.date
UNION
SELECT o.point, o.date, inc, out
FROM income_o i 
RIGHT JOIN outcome_o o on i.point = o.point and i.date = o.date
```

## 30 

https://sql-ex.ru/learn_exercises.php?LN=30

```sql
SELECT point, date, SUM(sum_out), SUM(sum_inc)
FROM( select point, date, SUM(inc) as sum_inc, null as sum_out 
FROM Income 
GROUP BY point, date
UNION
SELECT point, date, null as sum_inc, SUM(out) as sum_out 
FROM Outcome 
GROUP BY point, date ) as t
GROUP BY point, date 
ORDER BY point
```

## 31

https://sql-ex.ru/learn_exercises.php?LN=31

```sql
SELECT class, country 
FROM classes 
WHERE bore >= '16'
```

## 32

https://sql-ex.ru/learn_exercises.php?LN=32

```sql
SELECT country, cast(avg((power(bore,3)/2)) as numeric(6,2)) as weight 
FROM (select country, classes.class, bore, name 
FROM classes 
LEFT JOIN ships ON classes.class=ships.class  
UNION ALL
SELECT distinct country, class, bore, ship 
FROM classes t1 
LEFT JOIN outcomes t2 ON t1.class=t2.ship  
WHERE ship=class and ship not in (select name from ships) ) a  
WHERE name!='null' 
GROUP BY country
```

## 33

https://sql-ex.ru/learn_exercises.php?LN=33

```sql
SELECT ship 
FROM outcomes,battles 
WHERE result= 'sunk' and battle = 'North Atlantic' 
GROUP BY ship  
```

## 34

https://sql-ex.ru/learn_exercises.php?LN=34

```sql
SELECT name 
FROM classes,ships 
WHERE launched >=1922 and displacement>35000 and type='bb' and ships.class = classes.class 
```

## 35

https://sql-ex.ru/learn_exercises.php?LN=35

```sql
SELECT name 
FROM classes,ships 
WHERE launched >=1922 and displacement>35000 and type='bb' and ships.class = classes.class 
```

## 36

https://sql-ex.ru/learn_exercises.php?LN=36

```sql
SELECT distinct c.class 
FROM classes c 
JOIN outcomes o ON c.class = o.ship
UNION
SELECT distinct c.class 
FROM classes c join ships s ON c.class = s.class 
WHERE s.class = s.name
```

## 37

https://sql-ex.ru/learn_exercises.php?LN=37

```sql
SELECT class FROM(select class, name FROM ships
UNION
SELECT class, ship as name 
FROM outcomes 
JOIN classes ON classes.class = outcomes.ship) as A
GROUP BY class 
HAVING count(A.name)=1
```

## 38

https://sql-ex.ru/learn_exercises.php?LN=38

```sql
SELECT country FROM classes where type = 'bb'
INTERSECT
SELECT country FROM classes where type = 'bc'
```

## 39

https://sql-ex.ru/learn_exercises.php?LN=39

```sql
SELECT distinct o.ship 
FROM outcomes o join battles b ON o.battle = b.name 
WHERE o.result = 'damaged' AND EXISTS (SELECT battles.date
FROM battles join outcomes ON outcomes.battle = battles.name
WHERE battles.date > b.date and outcomes.ship = o.ship)
```

## 40

https://sql-ex.ru/learn_exercises.php?LN=40

```sql
SELECT maker, type 
FROM product
WHERE maker in (SELECT maker FROM
(SELECT maker, type FROM Product GROUP BY maker, type) Alias
GROUP BY maker having count(maker) = 1) GROUP BY maker, type HAVING count(type)>1
```

## 41

https://sql-ex.ru/learn_exercises.php?LN=41

```sql
WITH D as
(SELECT model, price FROM PC
UNION
SELECT model, price FROM Laptop
UNION
SELECT model, price FROM Printer)
SELECT distinct P.maker,
CASE WHEN MAX(CASE WHEN D.price IS NULL THEN 1 ELSE 0 END) = 0 THEN
max(D.price) end
FROM Product P
RIGHT JOIN D ON P.model=D.model
GROUP BY P.maker
```

## 42

https://sql-ex.ru/learn_exercises.php?LN=42

```sql
SELECT 
	ship, battle
FROM Outcomes
WHERE result = 'sunk'
```

## 43

https://sql-ex.ru/learn_exercises.php?LN=43

```sql
SELECT name 
FROM battles 
WHERE DATEPART(yy, date) not in (select DATEPART(yy, date)  
FROM battles 
JOIN ships on DATEPART(yy, date)=launched)
```

## 44

https://sql-ex.ru/learn_exercises.php?LN=44

```sql
SELECT name 
FROM ships 
WHERE name like 'R%'   
UNION   
SELECT name 
FROM battles 
WHERE name like 'R%'   
UNION   
SELECT ship 
FROM outcomes 
WHERE ship like 'R%'
```

## 45

https://sql-ex.ru/learn_exercises.php?LN=45

```sql
SELECT name 
FROM ships 
WHERE name like '% % %'  
UNION   
SELECT ship 
FROM outcomes 
WHERE ship like '% % %'  
```

## 46

https://sql-ex.ru/learn_exercises.php?LN=46

```sql
SELECT name as n, displacement as d, numguns as ng 
FROM ships 
INNER JOIN classes ON ships.class=classes.class 
WHERE name in (SELECT ship FROM outcomes WHERE battle = 'Guadalcanal')   
UNION 
SELECT ship as n, displacement as d, numguns as ng 
FROM outcomes
INNER JOIN classes ON outcomes.ship=classes.class 
WHERE battle = 'Guadalcanal' and ship not in (select name from ships)   
UNION  
SELECT ship as n, null as d, null as ng 
FROM outcomes 
WHERE battle = 'Guadalcanal' and ship not in (select name from ships) and ship not in  (select class from classes)     
```

## 47

https://sql-ex.ru/learn_exercises.php?LN=47

```sql
WITH out AS (SELECT *
FROM outcomes JOIN (SELECT ships.name s_name, classes.class s_class, classes.country s_country
FROM ships FULL JOIN classes
ON ships.class = classes.class
) u
ON outcomes.ship=u.s_class
UNION
SELECT *
FROM outcomes JOIN (SELECT ships.name s_name, classes.class s_class, classes.country s_country
FROM ships FULL JOIN classes
ON ships.class = classes.class
) u
ON outcomes.ship=u.s_name)
SELECT fin.country
FROM (
SELECT DISTINCT t.country, COUNT(t.name) AS num_ships
FROM (
SELECT distinct c.country, s.name
FROM classes c
INNER JOIN Ships s ON s.class= c.class
UNION
SELECT distinct c.country, o.ship
FROM classes c
INNER JOIN Outcomes o on o.ship= c.class) t
GROUP BY t.country
INTERSECT
SELECT out.s_country, COUNT(out.ship) AS num_ships
FROM out
WHERE out.result='sunk'
GROUP BY out.s_country) fin   
```

## 48

https://sql-ex.ru/learn_exercises.php?LN=48

```sql
SELECT class
FROM classes t1 
LEFT JOIN outcomes t2 on t1.class=t2.ship 
WHERE result='sunk'
UNION
SELECT class
FROM ships 
LEFT JOIN outcomes on ships.name=outcomes.ship 
WHERE result='sunk'
```

## 49

https://sql-ex.ru/learn_exercises.php?LN=49

```sql

SELECT s.name 
FROM ships s 
JOIN classes c ON s.name=c.class OR s.class = c.class 
WHERE c.bore = 16
UNION
SELECT o.ship 
FROM outcomes o 
JOIN classes c on o.ship=c.class
WHERE c.bore = 16
  
```

## 50

https://sql-ex.ru/learn_exercises.php?LN=50

```sql

SELECT distinct o.battle 
FROM ships s 
JOIN outcomes o on s.name = o.ship 
WHERE s.class = 'kongo'

```

## 51

https://sql-ex.ru/learn_exercises.php?LN=51

```sql


SELECT NAME 
FROM(select name as NAME, displacement, numguns from ships inner join classes on ships.class = classes.class union select ship as NAME, displacement, numguns from outcomes inner join classes on outcomes.ship= classes.class) as d1 inner join (select displacement, max(numGuns) as numguns from ( select displacement, numguns from ships inner join classes on ships.class = classes.class union select displacement, numguns from outcomes inner join classes on outcomes.ship= classes.class) as f group by displacement) as d2 on d1.displacement=d2.displacement and d1.numguns =d2.numguns
  
```

## 52

https://sql-ex.ru/learn_exercises.php?LN=52

```sql
SELECT s.name 
FROM ships s 
JOIN classes c on s.class = c.class 
WHERE country = 'japan' and (numGuns >= '9' or numGuns is null) and (bore < '19' or bore is null) and (displacement <= '65000' or displacement is null) and type='bb'
  
```

## 53

https://sql-ex.ru/learn_exercises.php?LN=53

```sql

SELECT CAST(AVG(numguns*1.0) AS NUMERIC(6,2)) as Avg_nmg 
FROM classes 
WHERE type = 'bb'
```

## 54

https://sql-ex.ru/learn_exercises.php?LN=54

```sql

    SELECT CAST(AVG(numguns*1.0) AS NUMERIC(6,2)) as AVG_nmg from (select ship, numguns, type from Outcomes join classes on ship = class
UNION
SELECT name, numguns, type 
FROM ships s 
JOIN classes c on c.class = s.class) as x 
WHERE type = 'bb'

```

## 55

https://sql-ex.ru/learn_exercises.php?LN=55

```sql

SELECT c.class, min(s.launched) 
FROM classes c 
LEFT JOIN ships s on c.class = s.class 
GROUP BY c.class

```

## 56

https://sql-ex.ru/learn_exercises.php?LN=56

```sql


SELECT c.class, COUNT(s.ship)
FROM classes c
LEFT JOIN (SELECT o.ship, sh.class
FROM outcomes o
LEFT JOIN ships sh ON sh.name = o.ship
WHERE o.result = 'sunk') AS s ON s.class = c.class OR s.ship = c.class
GROUP BY c.class
  
```

## 57

https://sql-ex.ru/learn_exercises.php?LN=57

```sql


SELECT class, COUNT(ship) count_sunked
FROM (SELECT name, class FROM ships
UNION
SELECT ship, ship FROM outcomes) t
LEFT JOIN outcomes ON name = ship AND result = 'sunk'
GROUP BY class
HAVING COUNT(ship) > 0 AND COUNT(*) > 2
  
```

## 58

https://sql-ex.ru/learn_exercises.php?LN=58

```sql


SELECT m, t,
CAST(100.0*cc/cc1 AS NUMERIC(5,2))
FROM
(SELECT m, t, sum(c) cc from
(SELECT distinct maker m, 'PC' t, 0 c from product
union all
SELECT distinct maker, 'Laptop', 0 from product
union all
SELECT distinct maker, 'Printer', 0 from product
union all
SELECT maker, type, count(*) from product
group by maker, type) as tt
group by m, t) tt1
JOIN (
SELECT maker, count(*) cc1 from product group by maker
) tt2
ON m=maker
  
```

## 59

https://sql-ex.ru/learn_exercises.php?LN=59

```sql

SELECT c1, c2-
(CASE
WHEN o2 is null THEN 0
ELSE o2
END)
from
(SELECT point c1, sum(inc) c2 FROM income_o
group by point) as t1
left join
(SELECT point o1, sum(out) o2 FROM outcome_o
group by point) as t2
on c1=o1
  
```

## 60

https://sql-ex.ru/learn_exercises.php?LN=60

```sql

SELECT c1, c2-
(CASE
WHEN o2 is null THEN 0
ELSE o2
END)
from
(SELECT point c1, sum(inc) c2 FROM income_o
where date<'2001-04-15'
group by point) as t1
left join
(SELECT point o1, sum(out) o2 FROM outcome_o
where date<'2001-04-15'
group by point) as t2
on c1=o1
  
```

## 61

https://sql-ex.ru/learn_exercises.php?LN=61

```sql

SELECT sum(i) FROM
(SELECT point, sum(inc) as i FROM
income_o
group by point
UNION
SELECT point, -sum(out) as i FROM
outcome_o
group by point
) as t
  
```

## 62

https://sql-ex.ru/learn_exercises.php?LN=62

```sql

SELECT
(SELECT sum(inc) FROM Income_o WHERE date<'2001-04-15')
-
(SELECT sum(out) FROM Outcome_o WHERE date<'2001-04-15')
AS remain

```

## 63

https://sql-ex.ru/learn_exercises.php?LN=63

```sql

 
SELECT name FROM Passenger
WHERE ID_psg in
(SELECT ID_psg FROM Pass_in_trip
GROUP BY place, ID_psg
HAVING count(*)>1)
  

```

## 64

https://sql-ex.ru/learn_exercises.php?LN=64

```sql

SELECT i1.point, i1.date, 'inc', sum(inc) FROM Income,
(SELECT point, date FROM Income
EXCEPT
SELECT Income.point, Income.date FROM Income
JOIN Outcome ON (Income.point=Outcome.point) AND
(Income.date=Outcome.date)
) AS i1
WHERE i1.point=Income.point AND i1.date=Income.date
GROUP BY i1.point, i1.date
UNION
SELECT o1.point, o1.date, 'out', sum(out) FROM Outcome,
(SELECT point, date FROM Outcome
EXCEPT
SELECT Income.point, Income.date FROM Income
JOIN Outcome ON (Income.point=Outcome.point) AND
(Income.date=Outcome.date)
) AS o1
WHERE o1.point=Outcome.point AND o1.date=Outcome.date
GROUP BY o1.point, o1.date

```

## 65

https://sql-ex.ru/learn_exercises.php?LN=65

```sql

SELECT row_number() over(ORDER BY maker,s),t, type FROM
(SELECT maker,type,
CASE
WHEN type='PC'
THEN 0
WHEN type='Laptop'
THEN 1
ELSE 2
END AS s,
CASE
WHEN type='Laptop' AND (maker in (SELECT maker FROM Product WHERE
type='PC'))
THEN 
WHEN type='Printer' AND ((maker in (SELECT maker FROM Product WHERE
type='PC')) OR (maker in (SELECT maker FROM Product WHERE
type='Laptop')))
THEN ''
ELSE maker
END AS t
FROM Product
GROUP BY maker,type) AS t1
ORDER BY maker, s

```

## 66

https://sql-ex.ru/learn_exercises.php?LN=66

```sql

SELECT date, max(c) FROM
(SELECT date,count(*) AS c FROM Trip,
(SELECT trip_no,date FROM Pass_in_trip WHERE date>='2003-04-01' AND date<='2003-04-07' GROUP BY trip_no, date) AS t1
WHERE Trip.trip_no=t1.trip_no AND town_from='Rostov'
GROUP BY date
UNION ALL
SELECT '2003-04-01',0
UNION ALL
SELECT '2003-04-02',0
UNION ALL
SELECT '2003-04-03',0
UNION ALL
SELECT '2003-04-04',0
UNION ALL
SELECT '2003-04-05',0
UNION ALL
SELECT '2003-04-06',0
UNION ALL
SELECT '2003-04-07',0) AS t2
GROUP BY date

```

## 67

https://sql-ex.ru/learn_exercises.php?LN=67

```sql

SELECT count(*) 
FROM
(SELECT TOP 1 WITH TIES count(*) c, town_from, town_to from trip
GROUP BY town_from, town_to
ORDER BY c desc) as t;

```

## 68

https://sql-ex.ru/learn_exercises.php?LN=68

```sql

SELECT count(*) 
FROM (
SELECT TOP 1 WITH TIES sum(c) cc, c1, c2 from (
SELECT count(*) c, town_from c1, town_to c2 
FROM trip
WHERE town_from>=town_to
GROUP BY town_from, town_to
union all
SELECT count(*) c,town_to, town_from 
FROM trip
WHERE town_to>town_from
GROUP BY town_from, town_to
) as t
GROUP BY c1,c2
ORDER BY cc desc
) as tt;
  
```

## 69

https://sql-ex.ru/learn_exercises.php?LN=69

```sql

WITH q as (
  SELECT
    isnull(i.point, o.point) point
    , isnull(i.date, o.date) date
    , coalesce(sum(i.inc), 0) - coalesce(sum(o.out), 0) balance
    FROM income i
    full join outcome o
      on i.point=o.point and i.date=o.date and i.code=o.code
    GROUP BY isnull(i.point, o.point), isnull(i.date, o.date)
)
SELECT
  point
    -- 103 means format "dd/mm/yyyy"
  , convert(varchar, date, 103) day
  , sum(balance) over(partition by point order by date RANGE UNBOUNDED PRECEDING) as rem
  FROM q
ORDER BY point,date
```
## 70

https://sql-ex.ru/learn_exercises.php?LN=70

```sql

SELECT DISTINCT o.battle
FROM outcomes o
LEFT JOIN ships s ON s.name = o.ship
LEFT JOIN classes c ON o.ship = c.class OR s.class = c.class
WHERE c.country IS NOT NULL
GROUP BY c.country, o.battle
HAVING COUNT(o.ship) >= 3;
  
```





