## Intermediate SQL

#### Count + Distinct
`SELECT COUNT(DISTINCT birthdate) AS count_distinct_birthdates FROM people;`

* Count only displays non-null values
* Order of exexcution --> FROM -> WHERE -> SELECT -> LIMIT
* Hence don't use alias in select cause in where clause, due to exec. order
* Round(var, no. of dp) : positive --> decimals, negative --> count from left (whole part)
