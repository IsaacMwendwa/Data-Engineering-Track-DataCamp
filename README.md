## Intermediate SQL

#### Count + Distinct
`SELECT COUNT(DISTINCT birthdate) AS count_distinct_birthdates FROM people;`

* Count only displays non-null values
* Order of exexcution -->
FROM -> WHERE -> GROUP BY -> HAVING -> SELECT -> AS (Alias) -> ORDER BY -> LIMIT
* Hence don't use alias in select cause in where clause, due to exec. order
* Round(var, no. of dp) : positive --> decimals, negative --> count from left (whole part)
* Agg Functions for Numbers --> COUNT, SUM, AVG, MAX, MIN ::: For Strings --> MAX, MIN, COUNT



#### Group By
Find the release_year and film_count of each year
* `SELECT release_year, COUNT(*) AS film_count
FROM films
GROUP BY release_year;`

Which release_year had the most language diversity?
* `SELECT release_year,
COUNT(DISTINCT language) AS most_language_diversity 
FROM films
GROUP BY release_year
ORDER BY most_language_diversity DESC;`

* To filter by Agg Funcs when grouping, you must use HAVING, not WHERE
* WHERE filters individual records, HAVING filters grouped records
* Order of Group BY Clauses: W G H O

#### JOINS
Write SELECT statement last after FROM and JOIN, to use table aliases defined in FROM/JOIN blocks
* `SELECT c.name AS country, l.name AS language, official
FROM countries AS c
INNER JOIN languages AS l
USING (code);`

Chaining Joins
* `SELECT name, e.year, fertility_rate, e.unemployment_rate
FROM countries AS c
INNER JOIN populations as p
ON c.code=p.country_code
INNER JOIN economies AS e
USING(code)`

Your task is to determine the top 10 capital cities in Europe and the Americas by city_perc, a metric you'll calculate. city_perc is a percentage that calculates the "proper" population in a city as a percentage of the total population in the wider metro area, as follows:

city_proper_pop / metroarea_pop * 100

Do not use table aliasing in this exercise.
`--Select fields from cities
SELECT name, country_code, city_proper_pop, metroarea_pop,
(city_proper_pop / metroarea_pop * 100) AS city_perc 
FROM cities
-- Use subquery to filter city name
WHERE name IN
(SELECT cities.name FROM cities
INNER JOIN countries
ON countries.capital = cities.name
WHERE continent ='Europe' OR continent LIKE '%America')
-- Add filter condition such that metroarea_pop does not have null values
AND metroarea_pop IS NOT NULL
-- Sort and limit the result
ORDER BY city_perc DESC LIMIT 10;`

#### Insert Distinct Records into New Tables
`INSERT INTO target_table 
SELECT DISTINCT col1, col2
FROM source_table;`

#### Normal Insert
`INSERT INTO table (col1, col2)
VALUES ("val_a", "val_b");`

#### Rename Column
`ALTER TABLE table RENAME COLUMN old_name TO new_name;`

#### Integrity Constraints
* Attribute constraints e.g data types on cols
* Key constraints e.g primary keys
* Referential Integrity cons -> enforced through foreign keys

  1. Attribute COnstraints
* Type Cast cols in query: `SELECT CAST(col AS integer) FROM table;'
* Type cast col in table: `ALTER TABLE table_name ALTER COLUMN column_name TYPE varchar(10) `
* Convert types without reserving too much space: `ALTER TABLE table_name ALTER COLUMN column_name TYPE varchar(x) USING SUBSTRING(column_name FROM 1 FOR x)`
 
  2. 

  3.


