# CARS ONLINE SQL PROJECT 
## Questions and Answers

**Author**: Aytekin Can

**Email**: aytekincan92@gmail.com

**LinkedIn**: https://www.linkedin.com/in/aytekincan

A SQL analysis of cars sold on Carsonline and the prices of car models by year, the average price of each transmission, number of hybrid cars for each car make, manual-gearbox cars by each car year and customers information such as number of customers by each gender and age and what are the countries of these customers.

#### Displaying the car id, price, car model, and car year for each car ORDER BY price?
````sql
SELECT c.car_id, c.price, ct.car_make, ct.car_model, ct.car_year 
FROM cars c JOIN car_types ct 
ON   c.car_type_id = ct.car_type_id 
ORDER BY price DESC
````
**Results:**

car_id|	price|car_make|car_model|car_year|
-------|-------|------------|-------------|----------|
55927|	159999|mercedes|G Class|2020|

#### Only cars made by bmw between 2015 - 2019?
````sql
SELECT TOP 10 c.car_id, c.price, ct.car_make, ct.car_model, ct.car_year 
FROM cars c 
INNER JOIN car_types ct 
ON c.car_type_id = ct.car_type_id
WHERE ct.car_make = 'bmw' 
AND ct.car_year = 2019
ORDER BY price DESC

````
**Results:**
car_id|	price|car_make|car_model|car_year|
-------|-------|------------|-------------|----------|
12481|	88980|	bmw| 8 Series|2019|
17114|	78386|	bmw|X7|2019|
13606|	77880|	bmw|X7|2019|
11477|	74990|	bmw|X7|2019|
12516|	74480|	bmw|X7|2019|
17680|	73990|	bmw|M5|2019|
15995|	73950|	bmw|X7|2019|
20496|	72000|	bmw| i8|2019|
17653|	69995|	bmw|X5|2019|
20652|	69948|	bmw|M5|2019|
#### Average price of audi models for the 2018?
````sql
SELECT ct.car_model, AVG(c.price) AS 'average_price'
FROM cars c JOIN car_types ct 
ON   c.car_type_id = ct.car_type_id
WHERE ct.car_make = 'audi' AND ct.car_year = 2020
GROUP BY ct.car_model
````
**Results:**
car_model|average_price|
-------------|-----------------|
 A1|23781|
 A3|26275|
 A4|36920|
 A5|31766|
 A7|45890|
 A8|49800|
 Q2|28634|
 Q3|33073|
 Q5|41146|
 Q7|63179|
 R8|133900|
 RS3|42490|
 SQ5|56450|
 TT|37425|

#### The number of cars by each fuel type name  and sort output by the numbers of cars descending? 
````sql
SELECT ft.fuel_type_name, COUNT(*) AS 'number_of_cars'
FROM cars c JOIN fuel_types ft 
ON   c.fuel_type_id = ft.fuel_type_id
GROUP BY ft.fuel_type_name
ORDER BY COUNT(*) DESC
````
**Results:**
fuel_type_name|number_of_cars|
--------------|--------------|
Petrol|7900|
Diesel|6673|
Hybrid|	564|
Other|31|
Electric|2|

#### Average price for each transmission name. Output by the average price 	?
````sql
SELECT tt.transmission_name, AVG(c.price) AS 'average_price' 
FROM cars c JOIN transmission_types tt 
ON   c.transmission_type_id = tt.transmission_type_id
GROUP BY tt.transmission_name
ORDER BY AVG(c.price) DESC````
**Results:**
transmission_name|average_price|
----------------|------------|
Semi-Auto|25200|
Automatic|21703|
Manual|12381|

#### Number of hybrid cars for each car make. Sort the output by the number of cars?
````sql
SELECT ct.car_make, COUNT(DISTINCT ct.car_model) AS 'number_of_hybrid_cars' 
FROM cars c JOIN fuel_types ft 
ON   c.fuel_type_id = ft.fuel_type_id
			JOIN car_types ct 
ON   c.car_type_id = ct.car_type_id
WHERE ft.fuel_type_name = 'Hybrid'
GROUP BY car_make
ORDER BY COUNT(DISTINCT car_model) DESC
````
**Results:**
car_make|number_of_hybrid_cars|
--------|---------------------|
bmw|7|
toyota|	7|
mercedes|4|
hyundi|	3|
audi|2|
ford|2|
skoda|1|

#### What is the number of customers by each gender?
````sql
SELECT g.gender, COUNT(*) AS 'number_of_customers'
FROM customers c JOIN genders g
ON   c.gender_code = g.gender_code
GROUP BY g.gender
````
**Results:**
gender|number_of_customers|
---------|----------------------------|
Female|2849|
Male|6151|







