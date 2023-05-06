# KateJiayi-Bi
Google Data Analytics Certificate Case Study1
###
To combine all the data in different files, what I did is:
###
SELECT 
  * 
FROM 
  cryptic-album-385521.divvytripdata.202101divvytripdata
UNION ALL
SELECT 
*
FROM
  cryptic-album-385521.divvytripdata.202102divvytripdata
UNION ALL
SELECT 
*
FROM
  cryptic-album-385521.divvytripdata.202103divvytripdata
UNION ALL
SELECT 
*
FROM
  cryptic-album-385521.divvytripdata.202104divvytripdata
UNION ALL
SELECT 
*
FROM
  cryptic-album-385521.divvytripdata.202105divvytripdata
UNION ALL
SELECT 
*
FROM
  cryptic-album-385521.divvytripdata.202106divvytripdata
UNION ALL
SELECT 
*
FROM
  cryptic-album-385521.divvytripdata.202107divvytripdata
UNION ALL
SELECT 
*
FROM
  cryptic-album-385521.divvytripdata.202108divvytripdata
UNION ALL
SELECT 
*
FROM
  cryptic-album-385521.divvytripdata.202109divvytripdata
UNION ALL
SELECT 
*
FROM
  cryptic-album-385521.divvytripdata.2021010divvytripdata
UNION ALL
SELECT 
*
FROM
  cryptic-album-385521.divvytripdata.2021011divvytripdata
UNION ALL
SELECT 
*
FROM
  cryptic-album-385521.divvytripdata.2021012divvytripdata
  
###
To clean the data(find errors in data) and extract information from data, here is what I did:



###
SELECT
  *,
  CASE
    WHEN EXTRACT(DayofWeek from started_at)=1 Then 'Sunday'
    WHEN EXTRACT(DayofWeek from started_at)=2 Then 'Monday'
    WHEN EXTRACT(DayofWeek from started_at)=3 Then 'Tuesday'
    WHEN EXTRACT(DayofWeek from started_at)=4 Then 'Wednesday'
    WHEN EXTRACT(DayofWeek from started_at)=5 Then 'Thursday'
    WHEN EXTRACT(DayofWeek from started_at)=6 Then 'Friday'
    ELSE 'Saturday'
  END AS day_of_week,
  EXTRACT(hour from started_at) as start_time,
  EXTRACT(month from started_at) as start_month,
  ABS(TIMESTAMP_DIFF(started_at,ended_at,second)) AS timedifference
FROM cryptic-album-385521.divvytripdata.2021divvytripdata
WHERE 
  ABS(TIMESTAMP_DIFF(started_at,ended_at,second)) > 0

