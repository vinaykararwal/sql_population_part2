# sql_population_part2
This is World Wide DATABASE from 2000 to 2010 . And i applied some common SQL queries on it.

**you already know how to setup from first part**

### Prerequsites
Basic SQL commnads or Operators only. :wink:


* First we will download our DATABASE from here [sql-population-queries-part-2-starting](https://codecademy-content.s3.amazonaws.com/PRO/independent-practice-projects/sql-population-queries/sql-population-queries-part-ii-starting.zip)

I think all set now we will do fun :wink:

### Let's Go

**This time our schema are**

---
`country`

| Columns | Type | notes |
| ----------- | ----------- |----------- |
| id | integer | primary key |
| name | text | 
| continent | text |

---

---
`population_years`

| Columns | Type | notes |
| ----------- | ----------- |----------- |
| id | integer | primary key |
| population | number| (in milions) |
| year | number |
| country_id | integer | foregin key |

---

#### Now its time to work on commands

1.**_To retrive all data from table_**
```
SEELCT * FROM countries;
SELECT * FROM population_years;
```


2.**_
How many entries in the countries table are from Africa?_**
```
SELECT count(*) FROM countries 
WHERE continent is 'Africa';
```
output is

---
| Count(*) | 
| ----------- | 
| 66|

---

3.**_What was the total population of the continent of Oceania in 2005?_**
```
SELECT SUM(population) FROM population_years
JOIN  countries
ON population_years.country_id = countries.id
WHERE countries.continent IS 'Oceania' AND year IS '2005';
```
output is

---
| sum(population) | 
| ----------- | 
| 32.66417|

---

4.**_
What is the average population of countries in South America in 2003?_**
```
SELECT AVG(population) FROM population_years
JOIN countries
ON population_years.country_id = countries.id
WHERE continent IS 'South America' AND year IS '2003';
```
output is

---
| Avg(population) | 
| ----------- | 
| 25.8906514285714|

---


5.**_
What country had the smallest population in 2007?_**
```
SELECT countries.name,MIN(population) FROM population_years
JOIN countries
ON population_years.country_id = countries.id
WHERE  year IS '2007';
```
output is

---
| name | min(population| 
| ----------- | ----------- |
| Niue | 0.00216 | 

---

6.**_
What is the average population of Poland during the time period covered by this dataset?_**
```
SELECT countries.name,AVG(population) FROM population_years
JOIN countries
ON population_years.country_id = countries.id
WHERE name IS 'Poland';
```
output is

---
| name | Avg(population| 
| ----------- | ----------- |
| Poland | 38.5606790909091 | 

---
7.**_
How many countries have the word “The” in their name?
_**
```
SELECT name, count(*) FROM countries
WHERE name LIKE '%The%'
GROUP BY name;
```
output is

---
| name | count(*)| 
| ----------- | ----------- |
| Bahamas, The | 1 | 
|Gambia, The| 1|
|Netherlands | 1|
|Netherlands Antilles|1|

---
`so total 4 countries have THE in their name.`

8.**_What was the total population of each continent in 2010?_**
```
SELECT continent,SUM(population) FROM population_years
JOIN countries
ON population_years.country_id = countries.id
WHERE year IS '2010'
GROUP BY continent;
```
output is

---
| continent | sum(population)| 
| ----------- | ----------- |
| Africa | 1015.47846 | 
|Asia| 4133.09148|
|Europe |723.06044|
|North America|539.79456|
|Oceania|34.95696|
|South America|396.58235|

---
**THANKS**
