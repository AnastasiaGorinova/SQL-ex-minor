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
+ [51](#51)
+ [52](#52)
+ [53](#53)
+ [54](#54)
+ [55](#55)
+ [56](#56)
+ [57](#57)
+ [58](#58)
+ [59](#59)
+ [60](#60)
+ [61](#61)
+ [62](#62)
+ [63](#63)
+ [64](#64)
+ [65](#65)
+ [66](#66)
+ [67](#67)
+ [68](#68)
+ [69](#69)
+ [70](#70)
+ [71](#71)
+ [72](#72)
+ [73](#73)
+ [74](#74)
+ [75](#75)
+ [76](#76)
+ [77](#77)
+ [78](#78)
+ [79](#79)
+ [80](#80)
+ [81](#81)
+ [82](#82)
+ [83](#83)
+ [84](#84)
+ [85](#85)
+ [86](#86)
+ [87](#87)
+ [88](#88)
+ [89](#89)
+ [90](#90)
+ [91](#91)
+ [92](#92)
+ [93](#93)
+ [94](#94)
+ [95](#95)
+ [96](#96)
+ [97](#97)
+ [98](#98)
+ [99](#99)
+ [100](#100)


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
ORDER BY c desc) as t

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
) as tt
  
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
HAVING COUNT(o.ship) >= 3
  
```

## 71

https://sql-ex.ru/learn_exercises.php?LN=71

```sql

SELECT p.maker
FROM product p
LEFT JOIN pc ON pc.model = p.model
WHERE p.type = 'PC'
GROUP BY p.maker
HAVING COUNT(p.model) = COUNT(pc.model)
  
```

## 72

https://sql-ex.ru/learn_exercises.php?LN=72

```sql

SELECT TOP 1 WITH TIES name, c3 
FROM passenger
JOIN
(SELECT c1, max(c3) c3 FROM
(
SELECT pass_in_trip.ID_psg c1, Trip.ID_comp c2, count(*) c3 FROM pass_in_trip
JOIN trip on trip.trip_no=pass_in_trip.trip_no
GROUP BY pass_in_trip.ID_psg, Trip.ID_comp
) as t
GROUP BY c1
HAVING count(*)=1) as tt
on ID_psg=c1
ORDER BY c3 desc

```

## 73

https://sql-ex.ru/learn_exercises.php?LN=73

```sql

SELECT DISTINCT c.country, b.name
FROM battles b, classes c
MINUS
SELECT c.country, o.battle
FROM outcomes o
LEFT JOIN ships s ON s.name = o.ship
LEFT JOIN classes c ON o.ship = c.class OR s.class = c.class
WHERE c.country IS NOT NULL
GROUP BY c.country, o.battle

```

## 74

https://sql-ex.ru/learn_exercises.php?LN=74

```sql

SELECT c.country, c.class
FROM classes c
WHERE UPPER(c.country) = 'RUSSIA' AND EXISTS (
SELECT c.country, c.class
FROM classes c
WHERE UPPER(c.country) = 'RUSSIA' )
UNION ALL
SELECT c.country, c.class
FROM classes c
WHERE NOT EXISTS (SELECT c.country, c.class
FROM classes c
WHERE UPPER(c.country) = 'RUSSIA' )

```

## 75

https://sql-ex.ru/learn_exercises.php?LN=75

```sql

SELECT shipname,launched,batname
FROM
(select s.name as shipname,launched,b.name as batname,
row_number() over (partition by s.name order by "date") as num
FROM ships s,battles b
WHERE to_char("date",'yyyy')>=launched
and launched is not null)
WHERE num = 1
UNION
(
SELECT name,launched,(select name from battles
WHERE "date" = (select max("date") from battles)) as batname
FROM ships
WHERE launched is null
)

```

## 76

https://sql-ex.ru/learn_exercises.php?LN=76

```sql

WITH cte AS
(SELECT ROW_NUMBER() OVER (PARTITION BY ps.ID_psg,pit.place ORDER BY pit.date) AS rowNumber
,DATEDIFF (minute, time_out, DATEADD(DAY,IIF(time_in<time_out,1,0),time_in)) AS timeFlight, ps.Id_psg, ps.name
FROM Pass_in_trip pit LEFT JOIN trip tr ON pit.trip_no = tr.trip_no
LEFT JOIN Passenger ps ON ps.ID_psg = pit.ID_psg -- Все рейсы
)
SELECT MAX(cte.name),SUM(timeFlight) FROM cte
GROUP BY cte.ID_psg
HAVING MAX(rowNumber) = 1

```


## 77

https://sql-ex.ru/learn_exercises.php?LN=77

```sql

SELECT TOP 1 WITH TIES * FROM (
  SELECT COUNT (DISTINCT P.trip_no) count, date
  FROM Pass_in_trip P
  JOIN Trip T ON T.trip_no = P.trip_no AND town_from = 'Rostov'
  GROUP BY P.trip_no, date) X
ORDER BY 1 DESC

```

## 78

https://sql-ex.ru/learn_exercises.php?LN=78

```sql

 SELECT name, REPLACE(CONVERT(CHAR(12), DATEADD(m, DATEDIFF(m,0,date),0), 102),'.','-') AS first_day,
             REPLACE(CONVERT(CHAR(12), DATEADD(s,-1,DATEADD(m, DATEDIFF(m,0,date)+1,0)), 102),'.','-') AS last_day
FROM Battles

```

## 79

https://sql-ex.ru/learn_exercises.php?LN=79

```sql

SELECT Passenger.name, A.minutes
FROM (SELECT P.ID_psg,
SUM((DATEDIFF(minute, time_out, time_in) + 1440)%1440) AS minutes,
MAX(SUM((DATEDIFF(minute, time_out, time_in) + 1440)%1440)) OVER() AS MaxMinutes
FROM Pass_in_trip P JOIN
Trip AS T ON P.trip_no = T.trip_no
GROUP BY P.ID_psg
) AS A JOIN
Passenger ON Passenger.ID_psg = A.ID_psg
WHERE A.minutes = A.MaxMinutes

```


## 80

https://sql-ex.ru/learn_exercises.php?LN=80

```sql

SELECT DISTINCT maker
FROM product
WHERE maker NOT IN (
SELECT maker
FROM product
WHERE type='PC' AND model NOT IN (
SELECT model
FROM PC))

```

## 81

https://sql-ex.ru/learn_exercises.php?LN=81

```sql 

SELECT O.*
FROM outcome O
INNER JOIN
(
SELECT TOP 1 WITH TIES YEAR(date) AS Y, MONTH(date) AS M, SUM(out) AS ALL_TOTAL
FROM outcome
GROUP BY YEAR(date), MONTH(date)
ORDER BY ALL_TOTAL DESC
) R ON YEAR(O.date) = R.Y AND MONTH(O.date) = R.M

```

## 82

https://sql-ex.ru/learn_exercises.php?LN=82

```sql 
WITH CTE(code,price,number)
AS
(
SELECT PC.code,PC.price, number= ROW_NUMBER() OVER (ORDER BY PC.code)
FROM PC
)
SELECT CTE.code, AVG(C.price)
FROM CTE
JOIN CTE C ON (C.number-CTE.number)<6 AND (C.number-CTE.number)> =0
GROUP BY CTE.number,CTE.code
HAVING COUNT(CTE.number)=6

```

## 84

https://sql-ex.ru/learn_exercises.php?LN=84

```sql 
SELECT C.name, A.N_1_10, A.N_11_21, A.N_21_30
FROM (SELECT T.ID_comp,
       SUM(CASE WHEN DAY(P.date) < 11 THEN 1 ELSE 0 END) AS N_1_10,
       SUM(CASE WHEN (DAY(P.date) > 10 AND DAY(P.date) < 21) THEN 1 ELSE 0 END) AS N_11_21,
       SUM(CASE WHEN DAY(P.date) > 20 THEN 1 ELSE 0 END) AS N_21_30
      FROM Trip AS T JOIN
       Pass_in_trip AS P ON T.trip_no = P.trip_no AND CONVERT(char(6), P.date, 112) = '200304'
      GROUP BY T.ID_comp
      ) AS A JOIN
 Company AS C ON A.ID_comp = C.ID_comp

```

## 85

https://sql-ex.ru/learn_exercises.php?LN=85

```sql 

SELECT maker
FROM product
GROUP BY maker
HAVING count(distinct type) = 1 and
       (min(type) = 'pc' or
       (min(type) = 'printer' and count(model) > 2))
  
```

## 86

https://sql-ex.ru/learn_exercises.php?LN=86

```sql 

SELECT maker,
CASE count(distinct type) when 2 then MIN(type) + '/' + MAX(type)
WHEN 1 then MAX(type)
WHEN 3 then 'Laptop/PC/Printer' END
FROM Product
GROUP BY maker
  
```

## 87

https://sql-ex.ru/learn_exercises.php?LN=87

```sql 

SELECT DISTINCT name, COUNT(town_to) Qty
FROM Trip tr JOIN Pass_in_trip pit ON tr.trip_no = pit.trip_no JOIN
         Passenger psg ON pit.ID_psg = psg.ID_psg
WHERE town_to = 'Moscow' AND pit.ID_psg NOT IN(SELECT DISTINCT ID_psg
FROM Trip tr JOIN Pass_in_trip pit ON tr.trip_no = pit.trip_no
WHERE date+time_out = (SELECT MIN (date+time_out)
                       FROM Trip tr1 JOIN Pass_in_trip pit1 ON tr1.trip_no = pit1.trip_no
                       WHERE pit.ID_psg = pit1.ID_psg)
AND town_from = 'Moscow')
GROUP BY pit.ID_psg, name
HAVING COUNT(town_to) > 1

```

## 88

https://sql-ex.ru/learn_exercises.php?LN=88

```sql 

SELECT
 (SELECT name FROM Passenger WHERE ID_psg = B.ID_psg) AS name,
 B.trip_Qty,
 (SELECT name FROM Company WHERE ID_comp = B.ID_comp) AS Company
FROM (SELECT P.ID_psg, MIN(T.ID_comp) AS ID_comp, COUNT(*) AS trip_Qty, MAX(COUNT(*)) OVER() AS Max_Qty
      FROM Pass_in_trip AS P JOIN
       Trip AS T ON P.trip_no = T.trip_no
      GROUP BY P.ID_psg
      HAVING MIN(T.ID_comp) = MAX(T.ID_comp)
      ) AS B
WHERE B.trip_Qty = B.Max_Qty

```

## 89

https://sql-ex.ru/learn_exercises.php?LN=89

```sql 

SELECT Maker , count(distinct model) Qty 
FROM Product
GROUP BY maker
HAVING count(distinct model) > = ALL
(select count(distinct model) 
FROM Product
group by maker)
or
count(distinct model) <= ALL
(select count(distinct model) from Product
GROUP by maker)

```

## 90

https://sql-ex.ru/learn_exercises.php?LN=90

```sql 

SELECT maker, model, type 
FROM
(
SELECT
row_number() over (order by model) p1,
row_number() over (order by model DESC) p2,
FROM Product
) t1
WHERE p1 > 3 and p2 > 3;

```

## 91

https://sql-ex.ru/learn_exercises.php?LN=91

```sql 

SELECT count(maker)
FROM product
WHERE maker in
(
  SELECT maker FROM product
  GROUP BY maker
  HAVING count(model) = 1
)

```

## 92

https://sql-ex.ru/learn_exercises.php?LN=92

```sql 

SELECT Q_NAME
FROM utQ
WHERE Q_ID IN (SELECT DISTINCT B.B_Q_ID
                FROM (SELECT B_Q_ID
                        FROM utB
                        GROUP BY B_Q_ID
                        HAVING SUM(B_VOL) = 765) AS B
                WHERE B.B_Q_ID NOT IN (SELECT B_Q_ID
                                        FROM utB
                                        WHERE B_V_ID IN (SELECT B_V_ID
                                                          FROM utB
                                                          GROUP BY B_V_ID
                                                          HAVING SUM(B_VOL) < 255)))

```

## 93

https://sql-ex.ru/learn_exercises.php?LN=93

```sql 


SELECT c.name, sum(vr.vr)
FROM
(select distinct t.id_comp, pt.trip_no, pt.date,t.time_out,t.time_in,--pt.id_psg,
case
WHEN DATEDIFF(mi, t.time_out,t.time_in)> 0 then DATEDIFF(mi, t.time_out,t.time_in)
WHEN DATEDIFF(mi, t.time_out,t.time_in)<=0 then DATEDIFF(mi, t.time_out,t.time_in+1)
end vr
FROM pass_in_trip pt left join trip t on pt.trip_no=t.trip_no
) vr LEFT JOIN join company c on vr.id_comp=c.id_comp
GROUP BY by c.name

```


## 94

https://sql-ex.ru/learn_exercises.php?LN=94

```sql 

SELECT DATEADD(day, S.Num, D.date) AS Dt,
       (SELECT COUNT(DISTINCT P.trip_no)
        FROM Pass_in_trip P
               JOIN Trip T
                 ON P.trip_no = T.trip_no
                    AND T.town_from = 'Rostov'
                    AND P.date = DATEADD(day, S.Num, D.date)) AS Qty
FROM (SELECT (3 * ( x - 1 ) + y - 1) AS Num
        FROM (SELECT 1 AS x UNION ALL SELECT 2 UNION ALL SELECT 3) AS N1
               CROSS JOIN (SELECT 1 AS y UNION ALL SELECT 2 UNION ALL SELECT 3) AS N2
        WHERE (3 * ( x - 1 ) + y ) < 8) AS S,
       (SELECT MIN(A.date) AS date
        FROM (SELECT P.date,
                       COUNT(DISTINCT P.trip_no) AS Qty,
                       MAX(COUNT(DISTINCT P.trip_no)) OVER() AS M_Qty
                FROM Pass_in_trip AS P
                       JOIN Trip AS T
                         ON P.trip_no = T.trip_no
                            AND T.town_from = 'Rostov'
                GROUP BY P.date) AS A
        WHERE A.Qty = A.M_Qty) AS D
```

## 95

https://sql-ex.ru/learn_exercises.php?LN=95

```sql 

SELECT name,
    COUNT(DISTINCT CONVERT(CHAR(24),date)+CONVERT(CHAR(4),Trip.trip_no)),
    COUNT(DISTINCT plane),
    COUNT(DISTINCT ID_psg),
    COUNT(*)
FROM Company,Pass_in_trip,Trip
WHERE Company.ID_comp=Trip.ID_comp and Trip.trip_no=Pass_in_trip.trip_no
GROUP BY Company.ID_comp,name

```

## 96

https://sql-ex.ru/learn_exercises.php?LN=96

```sql 

WITH r as (select v.v_name,
       v.v_id,
       count(case when v_color = 'R' then 1 end) over(partition by v_id) cnt_r,
       count(case when v_color = 'B' then 1 end) over(partition by b_q_id) cnt_b
  FROM utV v join utB b on v.v_id = b.b_v_id)
SELECT v_name
  FROM r
WHERE cnt_r > 1
  and cnt_b > 0
GROUP BY v_name;

```

## 97

https://sql-ex.ru/learn_exercises.php?LN=97

```sql 


SELECT code, speed, ram, price, screen
FROM laptop WHERE exists (
  SELECT 1 x
  FROM (
    SELECT v, rank()over(order by v) rn
    FROM ( select cast(speed as float) sp, cast(ram as float) rm,
                  cast(price as float) pr, cast(screen as float) sc
    )l unpivot(v for c in (sp, rm, pr, sc))u
  )l pivot(max(v) for rn in ([1],[2],[3],[4]))p
  WHERE [1]*2 <= [2] and [2]*2 <= [3] and [3]*2 <= [4]
)

```


## 98

https://sql-ex.ru/learn_exercises.php?LN=98

```sql 

WITH CTE AS
(select
1 n, cast (0 as varchar(16)) bit_or,
code, speed, ram FROM PC
UNION ALL
SELECT n*2,
cast (convert(bit,(speed|ram)&n) as varchar(1))+cast(bit_or as varchar(15))
, code, speed, ram
FROM CTE WHERE n < 65536
)
SELECT code, speed, ram 
FROM CTE
WHERE n = 65536
and CHARINDEX('1111', bit_or )> 0

```

## 99

https://sql-ex.ru/learn_exercises.php?LN=99

```sql 

SELECT point,
       "date" income_date,
       "date" + nvl(
                  min(case when diff > cnt then cnt else null end),
                  max(cnt)+1
                ) incass_date
FROM (select i.point,
             i."date",
             (trunc(o."date") - trunc(i."date")) diff, 
             count(1) over (partition by i.point, i."date" order by o."date" rows between unbounded preceding and current row)-1 cnt
      FROM income_o i
               JOIN (select point, "date", 1 disabled from outcome_o
                     UNION
                     SELECT point, trunc("date"+7,'DAY'), 1 disabled from income_o) o
                 on i.point = o.point
      WHERE o."date" > = i."date")
GROUP BY point, "date"

```

## 100

https://sql-ex.ru/learn_exercises.php?LN=100

```sql 

SELECT distinct A.date , A.R, B.point, B.inc, C.point, C.out
FROM (Select distinct date, ROW_Number() OVER(PARTITION BY date ORDER BY code asc) as R 
FROM Income
UNION 
SELECT distinct date, ROW_Number() OVER(PARTITION BY date ORDER BY code asc) From Outcome) A
LEFT JOIN (Select date, point, inc
                , ROW_Number() OVER(PARTITION BY date ORDER BY code asc) as RI FROM Income
           ) B on B.date=A.date and B.RI=A.R
LEFT JOIN (Select date, point, out
                , ROW_Number() OVER(PARTITION BY date ORDER BY code asc) as RO FROM Outcome
           ) C on C.date=A.date and C.RO=A.R;
  
```

