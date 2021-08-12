### Project Describtion
--------------------------
In This project I extracted the data from the databease that `Udacity` offered using the following queries 

To extract data from the `global_temp` table
```sql
( select * from global_data where year between 1940 and 2013 )
```
To extract data for my country `Riyadh` from `city_temp` table
```sql
( select * from city_Data where city = 'Riyadh' and year >= 1940 )
```
after that I merged the results into an `Excel` File to calculate the `Moving Average` and also to to draw a `Line Chart`  
