SQL
========================

## LIKE concat() with % wildcard

example - 
Find the capital and the name where the capital includes the name of the country.
```
SELECT capital, name
FROM world
WHERE capital LIKE concat('%', name, '%')
```

## extracting part of an existing string into a column

example - 

The capital of Monaco is Monaco-Ville: this is the name Monaco and the extension is -Ville.

Show the name and the extension where the capital is a proper (non-empty) extension of name of the country.

```
SELECT name, REPLACE(capital, name,'') as extension
FROM world
WHERE capital LIKE concat(name, '_', '%')

```

## Escaping single quotes

You can't put a single quote in a quote string directly. You can use two single quotes within a quoted string.

```
SELECT *
FROM nobel
WHERE winner = 'EUGENE O''NEILL'
```

## ORDER BY  with expressions

The expression subject IN ('chemistry','physics') can be used as a value - it will be 0 or 1.

Show the 1984 winners and subject ordered by subject and winner name; but list chemistry and physics last.

```
SELECT winner, subject
FROM nobel
WHERE yr=1984
ORDER BY 
CASE WHEN subject IN ('physics','chemistry') THEN 1 ELSE 0 END, subject,winner
```

## operated over a group of items in a column in WHERE

using ALL 

Which countries have a GDP greater than every country in Europe? [Give the name only.] (Some countries may have NULL gdp values)

```
SELECT name
FROM world
WHERE gdp > ALL(SELECT gdp FROM world WHERE continent = 'europe' AND gdp > 0)
```

## Self Comparison

Find the largest country (by area) in each continent, show the continent, the name and the area:

```
SELECT continent, name, area FROM world x
  WHERE area >= ALL
    (SELECT area FROM world y
        WHERE y.continent=x.continent
          AND area>0)

```

Some countries have populations more than three times that of all of their neighbours (in the same continent). Give the countries and continents.

```
SELECT name, continent
FROM world x
WHERE population > ALL (SELECT 3 * population FROM world y WHERE x.continent = y.continent AND x.name != y.name)
```

`x.continent = y.continent` - keeps the comparisons within a continent
`x.name != y.name` - compare with neighbours (not self)

world x and world y are mirrored

### Explaination

note - this is for one continent

| x.name | x.population | y.name | y.population |
|---|---|---|---|
| a | 15 | a | 15 |
| b | 1 | b | 1 |
| c | 7 | c | 7 |

1. x.a (15) checks with y.b * 3 (1 x 3 = 3), y.a is skipped because of `x.name != y.name` 
2. since x.a > y.a * 3, move on to next comparison
3. x.a(15) checks with y.c * 3 (7 x 3 = 21)
4. since x.a < y.c * 3, the ALL check returns false
5. move on to next continent


## ___ in each Continent (group)

```
SELECT continent, name, area FROM world x
  WHERE ___ >= ALL
    (SELECT ___ FROM world y
        WHERE y.continent=x.continent
          AND area>0)


```

## Counting duplicate rows

Show the year and subject where 3 prizes were given. Show only years 2000 onwards.

```
SELECT yr, subject
FROM nobel
WHERE yr >= 2000
GROUP BY yr, subject
HAVING COUNT(*) = 3
```

## Nested SELECTs

nested selects are not `JOIN`-ed yet

```
SELECT title, name
FROM casting
JOIN movie ON movie.id = casting.movieid
JOIN actor ON actor.id = casting.actorid
WHERE movieid IN (
  SELECT movieid FROM casting WHERE actorid IN (
    SELECT id FROM actor WHERE name = "Julie Andrews"
    )
  ) AND ord = 1

```

## Select first result of GROUP BY

use `MAX` in `SELECT`

```
SELECT yr-1812 as age, 
  MAX(CASE WHEN m12/10 < 0 THEN 'White Christmas' ELSE 'No Snow' END)
  FROM hadcet
  WHERE yr BETWEEN 1812 and 1812+12 AND (dy BETWEEN 21 AND 25)

GROUP BY age

```

## Using derived tables

A person's White Christmas Count (wcc) is the number of White Christmases they were exposed to as a child (between 3 and 12 inclusive assuming they were born at the beginning of the year and were about 1 year old on their first Christmas).

Charles Dickens's wcc was 8.

Assume CD was 1 in 1812

List all the years and the wcc for children born in each year of the data set. Only show years where the wcc was at least 7.

notes - `m12` is the temp for december. Temp  < 0 is a wc. `dy` is day

```
SELECT yob, COUNT(wc) AS wcc

FROM(SELECT yob, yr+1-yob as age, 
        CASE WHEN MIN(m12) < 0 THEN 'White Christmas' END AS wc
        FROM hadcet       
        JOIN (SELECT DISTINCT yr as yob FROM hadcet WHERE yr) AS y
        WHERE yr BETWEEN yob+2 and yob+11 AND dy BETWEEN 21 AND 25
        GROUP BY yob, age
     ) AS x
                
GROUP BY yob

HAVING COUNT(wc)>=7
```

Best way to solve this is to work on smaller problems first. Break the SELECT statement into parts and figure out how to get those columns. 
Make a query for one specific person (i.e. Charles Dickens) before scaling it to an entire table.

1. build a query to get White Christmases for one child (Charles Dickens) from age 3 to 12

!Important! - wc has to return null for non-white christmasses. if it returns 'no snow', it will be considered truthy

```
SELECT yr+1-1812 as age, 
  CASE WHEN MIN(m12) < 0 THEN 'White Christmas' END as wc
  FROM hadcet
  WHERE yr BETWEEN 1812+2 and 1812+12 AND (dy BETWEEN 21 AND 25)

GROUP BY age

```

2. build a query to get years of birth (yob)

```
SELECT DISTINCT yr as yob FROM hadcet WHERE yr
```

3. using the query in (1) as a derived table, count the number of wc . Derived tables need to have an alias

```
SELECT COUNT(wc) AS wcc

FROM(SELECT yr+1-1812 as age, 
        CASE WHEN MIN(m12) < 0 THEN 'White Christmas' END as wc
        FROM hadcet
        WHERE yr BETWEEN 1812+2 and 1812+12 AND (dy BETWEEN 21 AND 25)        
        GROUP BY age
     ) AS x
```

4. Make this apply to all yob in hadcet table, not just Charles Dickens. Join the derived table(1) to the query in (2), which will also be a derived table. Now we have a generalised yob column to replace 1812.

```
SELECT yob, COUNT(wc) AS wcc

FROM(SELECT yob, yr+1-yob as age, 
        CASE WHEN MIN(m12) < 0 THEN 'White Christmas' END AS wc
        FROM hadcet       
        JOIN (SELECT DISTINCT yr as yob FROM hadcet WHERE yr) AS y
        WHERE yr BETWEEN yob+2 and yob+11 AND dy BETWEEN 21 AND 25
        GROUP BY yob, age
     ) AS x
                
GROUP BY yob
```

5. Finally, add the final constrait of only showing years where the wcc was at least 7.

```
SELECT yob, COUNT(wc) AS wcc

FROM(SELECT yob, yr+1-yob as age, 
        CASE WHEN MIN(m12) < 0 THEN 'White Christmas' END AS wc
        FROM hadcet       
        JOIN (SELECT DISTINCT yr as yob FROM hadcet WHERE yr) AS y
        WHERE yr BETWEEN yob+2 and yob+11 AND dy BETWEEN 21 AND 25
        GROUP BY yob, age
     ) AS x
                
GROUP BY yob

HAVING COUNT(wc)>=7
```

