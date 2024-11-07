---
tags:
  - sql
date created: Sat, Mar 2nd 2024, 9:55 am
date modified: Sun, Nov 3rd 2024, 1:36 am
---

PostgreSQL using
```SQL
CREATE DATABASE NAME
```

| command line                                   | description                   |
| ---------------------------------------------- | ----------------------------- |
| \l <br><br>                                    | see the database              |
| \c name                                        | connect to specific database  |
| \d                                             | display all table in database |
| psql --username=freecodecamp --dbname=postgres |                               |

A`view` is a virtual table that is the result of a saved SQL SELECT statement
When accessed, views automatically update in response to updates in the underlying data
`view` is like creating a subtable of a large table, or orignal table
```sql
CREATE VIEW NAME AS
```

INTERMEDIATE SQLComparison operators
`>` Greater than or after
`<` Less than or before
`=` Equal to
`>=` Greater than or equal to
`<=` Less than or equal to
`<>` Not equal to

`LIKE `and `IS NOT LIKE`
%A  The last character is A
A%  The first character is A
_ _t% The third character is t

The syntax for counting unique values is `COUNT(DISTINCT field_name)`.
what is the difference between `SELECT DISTINCT COUNT(field_name)`

`COUNT(field_name)` includes only non-missing values
`COUNT(*)` includes missing values

`IS NULL` and `IS NOT NULL`

```sql
SELECT ROUND(AVG(budget),-5) AS avg_budget FROM films
# 后五位都为0
WHERE release_year >= 2010;
```
ROUND() is have a negative number as the decimal place parameter. This can come in handy if your manager only needs to know the average number to the hundreds since granularity below one hundred likes won't impact decision making.
`ROUND(,-3)` round to hundreds

HAVING vs WHERE
WHERE filters individual records, HAVING filters grouped records

What films were released in the year 2000?
```sql
SELECT title
FROM films
WHERE release_year = 2000;
```
In what years was the average film duration over two hours?
```sql
SELECT release_year
FROM films
GROUP BY release_year
HAVING AVG(duration) > 120;
```
write a query that returns the average budget and gross earnings for films each year after 1990 if the average budget is greater than 60 million.
```sql
SELECT release_year, AVG(budget) AS avg_budget, AVG(gross) AS avg_gross
FROM films
WHERE release_year > 1990
GROUP BY release_year
HAVING AVG(budget) > 60000000
-- Order the results from highest to lowest average gross and limit to one
ORDER BY avg_gross DESC LIMIT 1;
```

`INNER JOIN` looks for records in both tables which match on a given field

## except

result from the first query block to those rows which are (also) not found in the second query.

# case when

```sql
select 
	avg(selling_price) as average_selling_price, 
    count(*) as number_of_sells,
    substring(selling_date,12,4) as selling_year,
    case substring(selling_date,5,3)
		when 'Jan' then 1
        when 'Feb' then 2
        when 'Mar' then 3
        when 'Apr' then 4
        when 'May' then 5
        when 'Jun' then 6
        when 'Jul' then 7
        when 'Aug' then 8
        when 'Sep' then 9
        when 'Oct' then 10
        when 'Nov' then 11
        when 'Dec' then 12
	    else NULL
	end as selling_month
from car_prices
group by selling_month, selling_year
order by average_selling_price desc;
```
`substring(variable, start, length)` to extract the substring from the string variable given in the bracket. counting from 1

## having

`having` clause in `group by` won't keep the null values when you want some condition that is not related to null filtering. lets say, we want to keep non-c0 car conditions, including null. this time we should write as below:
```sql
having car_condition is null or car_condition !='c0'
```
if we dont add `car_conditon is null`, the result will automatically filter NULL values
The `IS NULL` condition is used to specifically include `NULL` values in the result set.

`join on/using` when only having `join` without any word like inner join, left join.., it just means `inner join`, where it matches common record in both table only

```sql
SELECT make, model, body, COUNT(*) AS number_of_sells
FROM car_prices
WHERE body = 'Sedan' AND state = 'ca'
GROUP BY make, model, body
ORDER BY number_of_sells DESC
LIMIT 5;
```
The operation ordering of this code is
`from`
`where`
`group by`
`select`
`order by`

**ANY_VALUE()**:
- The function `ANY_VALUE()` is used when you don't care which value is returned from a group. It picks an arbitrary value from the group without enforcing aggregation (such as `MAX()` or `MIN()`).

Make the null come last when sorting asc
https://stackoverflow.com/questions/1498648/sql-how-to-make-null-values-come-last-when-sorting-ascending

```sql
SELECT 
    cc.primary_description, 
    COUNT(*) AS number_of_crimes
FROM 
    chicago_crime AS cc
JOIN 
    chicago_socioeconomic AS cs 
ON 
    cc.community_area_number = cs.community_area_number
WHERE 
    cs.community_area_name = 'Lincoln Square'
GROUP BY 
    cc.primary_description
ORDER BY 
    number_of_crimes DESC
LIMIT 5;
```
operation order:
from
join
where
group by
select
order by
limit

- **Without `GROUP BY`**: `COUNT()` counts all the rows in the dataset, and there’s no need to group anything because you're treating the entire result set as a single group.
- **With `GROUP BY`**: `COUNT()` (or any other aggregate function) is applied **within** each group, so the `GROUP BY` is necessary to specify how to divide the rows into separate groups before counting or aggregating.

Order by without defined ascending or descending, it orders default by ascending