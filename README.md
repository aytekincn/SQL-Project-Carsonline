# CARS ONLINE SQL PROJECT 
## Questions and Answers

**Author**: Aytekin Can

**Email**: aytekincan92@gmail.com

**LinkedIn**: https://www.linkedin.com/in/aytekincan

A SQL analysis of cars sold on Carsonline and the prices of car models by year, the average price of each transmission, number of hybrid cars for each car make, manual-gearbox cars by each car year and customers information such as number of customers by each gender and age and what are the countries of these customers.

#### Displaying the car id, price, car model, and car year for each car ORDER BY price desc top 10?
````sql
SELECT c.car_id, c.price, ct.car_make, ct.car_model, ct.car_year 
FROM cars c JOIN car_types ct 
ON   c.car_type_id = ct.car_type_id 
ORDER BY price DESC
````
**Results:**

car_id|	price|car_make|car_model|car_year|
|-------|-------|------------|-------------|----------|
55927|159999|mercedes|G Class|2020|
49733|149948|mercedes|SL CLASS|2011|
5459|133900|audi|R8|2020
1646|129000|audi|R8|2019
55951|124999|mercedes|S Class|2019|
53822|124366|mercedes|A Class|2019|
4742|117990|audi|R8|2019|
5707|116000|audi|R8|2019|
56862|115359|mercedes|A Class|2019|
51708|109995|mercedes|S Class|2019|
