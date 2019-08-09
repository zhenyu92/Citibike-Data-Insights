# New York Citybike Data Insights Powered by Google Data Studio
This project is a part of the learning milestone of a Udemy course delivered by [Chris Levy](https://www.udemy.com/sql-for-data-science-with-google-big-query/). 

### Author
[Derrick Chan](https://github.com/zhenyu92)

[Linkedin](https://www.linkedin.com/in/zychan/)

### Project Status: [Completed]

### Project Objective
The study is on the dateset of largest bike sharing program in the United States. To produece an internal dashboard which highlights interesting data points, metrics, and visualizations from all the bike trips in the database.

### Environment Prerequisites
`Google Big Query` on `Google Cloud Platform`
`Google Data Studio`

### Instruction
Database can be accessed from the Big Query public data set:
`bigquery-public-data.new_york.citibike_trips`

##### First Dataset Query
```
SELECT
  CAST(starttime AS date) AS date,
  COUNT(*) AS num_trips,
  round(SUM(tripduration/60),2) AS total_duration_minutes,
  COUNT(DISTINCT bikeid) AS num_bikes
FROM
  `bigquery-public-data.new_york.citibike_trips`
GROUP BY
  date
ORDER BY
  date ASC
```

##### Second Dataset Query
```
SELECT
  CAST(starttime AS date) AS date,
  start_station_name,
  COUNT(*) AS num_trips,
  COUNT(DISTINCT bikeid) AS num_bikes,
  ROUND(SUM(tripduration/60),2) AS total_trip_duration_minutes
FROM
  `bigquery-public-data.new_york.citibike_trips`
GROUP BY
  date,
  start_station_name
ORDER BY
  date
```

##### Third Dataset Query
```
SELECT
  CAST(starttime AS date) AS date,
  usertype,
  gender,
  COUNT(*) AS num_trips,
  ROUND(SUM(tripduration/60),2) AS total_duration_minutes
FROM
  `bigquery-public-data.new_york.citibike_trips`
WHERE
  gender != 'unknown'
GROUP BY
  date,
  usertype,
  gender
ORDER BY
  date,
  usertype,
  gender
```

##### Forth Dataset Query
```
SELECT
  bikeid,
  CAST(starttime AS date) AS date,
  COUNT(*) AS num_trips,
  round(SUM(tripduration/60),2) AS total_duration_minutes
FROM
  `bigquery-public-data.new_york.citibike_trips`
GROUP BY
  date,
  bikeid
```

### Import & Tuning in Google Data Studio
Screenshot of the Dashboard: 
![alt text](https://github.com/zhenyu92/Citibike-Data-Insights/blob/master/Dashboard.jpg "Logo Title Text 1")
