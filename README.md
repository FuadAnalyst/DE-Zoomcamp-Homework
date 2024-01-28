# DE-Zoomcamp-Homework

### SQL questions:
3. select count(*)  
from green_taxi_data  
where date(lpep_pickup_datetime) = '2019-09-18'  
and date(lpep_dropoff_datetime) = '2019-09-18'

4. select date(lpep_pickup_datetime)  
from green_taxi_data  
where trip_distance = (select max(trip_distance) from green_taxi_data)

5. select zg."Zone", max(tip_amount)  
from zones_green zg inner join green_taxi_data gr  
on zg."LocationID" = gr."DOLocationID"  
where EXTRACT(YEAR FROM lpep_pickup_datetime) = 2019   
and EXTRACT(MONTH FROM lpep_pickup_datetime) = 9  
group by 1

6. select zg2."Zone" as dropoff_zones, gt."tip_amount"  
from green_taxi_data gt  
inner join zones_green zg1 on gt."PULocationID" = zg1."LocationID"  
inner join zones_green zg2 on gt."DOLocationID" = zg2."LocationID"  
where EXTRACT(YEAR FROM gt."lpep_pickup_datetime") = 2019   
AND EXTRACT(MONTH FROM gt."lpep_pickup_datetime") = 9  
AND zg1."Zone" = 'Astoria'  
ORDER BY 2 DESC  
