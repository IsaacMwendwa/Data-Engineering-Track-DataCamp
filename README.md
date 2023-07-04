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
