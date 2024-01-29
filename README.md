# Cyclistic Bike-Share Analysis Case Study

## Introduction
Welcome to the Cyclistic bike-share analysis case study !  
Cyclistic is a fictional bike-share company in Chicago. This company offers bike share program which allows people to rent bikes to ride based on their need and convenience. The company's future success depends on maximizing the number of annual memberships of the bike share program. Using the historical bike trips data provided by the company, in this case study we will try to understand how casual riders and annual members use Cyclistic bikes differently. From the insights we gain from the data and the trends we observe in the data visualizations, we will help the company design a new marketing strategy to convert casual riders into annual members for company's future growth and success.

## Table of Content
- [About the company](#about-the-company)
- [Business Task](#business-task)
- [Description of the data sources used in this analysis](#description-of-the-data-sources-used-in-this-analysis)
- [Tools and Technologies used in this analysis](#tools-and-technologies-used-in-this-analysis)
- [Documentation of cleaning or manipulation of data](#documentation-of-cleaning-or-manipulation-of-data)
- [Summary of My Data Analysis](#summary-of-my-data-analysis)
    - [Data Analysis using Google Sheets / Microsoft Excel](#data-analysis-using-google-sheets--microsoft-excel)
    - [Data Analysis using SQL and Google BigQuery](#data-analysis-using-sql-and-google-bigquery)
- [Supporting Visualizations and Key Findings](#supporting-visualizations-and-key-findings)
    - [Data Visualization using Google Sheets / Microsoft Excel](#data-visualization-using-google-sheets--microsoft-excel)
    - [Data Visualization using Tableau](#data-visualization-using-tableau)
    - [Data Visualization using R](#data-visualization-using-r)
    - [Key Findings from my Data Analysis](#key-findings-from-my-data-analysis)
- [My Recommendations based on the Analysis](#my-recommendations-based-on-the-analysis)

## About the company
In 2013, Cyclistic launched a successful bike-share offering. Since then, the program has grown to a fleet of 5,824 bicycles that are geotracked and locked into a network of 692 stations across Chicago. The bikes can be unlocked from one station and returned to any other station in the system anytime. Cyclistic users are more likely to ride for leisure, but about 30% use them to commute to work each day.  

Until now, Cyclistic’s marketing strategy relied on building general awareness and appealing to broad consumer segments. One approach that helped make these things possible was the flexibility of its pricing plans: single-ride passes, full-day passes, and annual memberships.  
- Customers who purchase single-ride or full-day passes are referred to as **casual** riders.
- Customers who purchase annual memberships are Cyclistic **members**.  

Cyclistic’s finance analysts have concluded that annual members are much more profitable than casual riders. Although the pricing flexibility helps Cyclistic attract more customers, The director of marketing (Lily Moreno) believes that maximizing the number of annual members will be key to future growth. Rather than creating a marketing campaign that targets all-new customers, she believes there is a very good chance to convert casual riders into members. She notes that casual riders are already aware of the Cyclistic program and have chosen Cyclistic for their mobility needs.  

Moreno has set a clear goal: Design marketing strategies aimed at converting casual riders into annual members. In order to do that, we need to understand how casual riders and annual members use Cyclistic bikes differently. From the insights gained from the data and the trends observed in the data visualizations, we will design a new marketing strategy to convert casual riders into annual members for company's future growth and success.

## Deliverables
1. A clear statement of the business task
2. A description of all data sources used
3. Documentation of any cleaning or manipulation of data
4. A summary of analysis
5. Supporting visualizations and key findings
6. Recommendations based on analysis


## Business Task
Understand how casual riders and annual members use Cyclistic bikes differently. From the insights gained from the data and the trends observed in the data visualizations, design a new marketing strategy to convert casual riders into annual members for company's future growth and success.

## Description of the data sources used in this analysis
We will use below historical bike trips data to analyze and identify trends. Below file contains data regarding all the bike trips done by the customers in the second half (i.e Between June to December) of the year 2013. This is public data that we can use to explore how different customer types are using Cyclistic bikes.  

https://divvy-tripdata.s3.amazonaws.com/Divvy_Stations_Trips_2013.zip  

( **Note** : The dataset have a different name because Cyclistic is a fictional company. For the purposes of this case study, the dataset is appropriate and will enable us to answer the business questions. The data has been made available by Lyft Bikes and Scooters, LLC under this [**License**](https://divvybikes.com/data-license-agreement) ).

## Tools and Technologies used in this analysis
1] Google Sheets / Microsoft Excel  
2] SQL  
3] Google BigQuery  
4] Tableau  
5] R programming Language  
6] RStudio (Posit Cloud)

## Documentation of cleaning or manipulation of data
Below is the Main Table which contains data regarding all the bike trips done by the customers in the second half (i.e Between June to December) of the year 2013 :  
[Divvy_Trips_2013.csv](https://drive.google.com/file/d/13pX4uFSOib5Olhm8voSLa1RT7aLs_5Pv/view?usp=sharing)  
The above table contains following columns :
- trip_id
- starttime
- stoptime
- bikeid
- tripduration
- from_station_id
- from_station_name
- to_station_id
- to_station_name
- usertype
- gender
- birthday

As a part of cleaning and manipulation of the data, to make our data analysis easy and convenient I removed several columns from the above **"Divvy_Trips_2013"** table which were not necessary or were not required in our analysis and added few new columns which could contribute better while analyzing the data.
  
Therefore I created a new table with name [Cyclistic_2013_Data.csv](https://drive.google.com/file/d/1vQ8cvs8qzLvy--BICxWY9jqrbYH35Ssm/view?usp=sharing) .  
All the data in the new table **"Cyclistic_2013_Data"** is imported from our Main table **"Divvy_Trips_2013"** , but the change is I did not import **bikeid, from_station_id, from_station_name, to_station_id, to_station_name, gender & birthday** columns and its data to my new table, as those columns and the data in it was not required during the process of data analysis.  

#### I added below 5 new columns to my new table "Cyclistic_2013_Data" because they contributed better to my analysis and made my data analysis process easy and convenient :
- tripduration_min ( contains total time duration of the bike trip in mins )
- weekday ( contains the number corresponding to the day of a week. for example Sunday is 1, Monday is 2 etc. )
- month ( contains the number corresponding to the month of a year. for example January is 1, June is 6 etc. )
- day_of_week ( contains day of a week. ex. Sunday, Monday etc. )
- month_name ( contains month of a year. ex. January , February, March etc. )

So now going forward we will only use our new table **"Cyclistic_2013_Data"** for data analysis. Below is the list of columns present in our new table :
- trip_id
- starttime
- stoptime
- tripduration_sec
- tripduration_min
- usertype
- weekday
- month
- day_of_week
- month_name


## Summary of My Data Analysis

### Data Analysis using Google Sheets / Microsoft Excel
- Imported [Cyclistic_2013_Data.csv](https://drive.google.com/file/d/1vQ8cvs8qzLvy--BICxWY9jqrbYH35Ssm/view?usp=sharing) into a Google sheet.

![Snapshot](https://github.com/moheenpatel/Cyclistic-bike-share-analysis/assets/72771390/d5364d1a-f399-4b65-ae55-d9d7c603fd6e)

- Used **Pivot Table** to fetch below 3 Information from the **"Cyclistic_2013_Data"** table

1] Total number of Bike Trips done by Casual rider and Annual Member by Month in the second half (i.e Between June to December) of the year 2013
![screenshot 1](https://github.com/moheenpatel/Cyclistic-bike-share-analysis/assets/72771390/e38ef990-f8f4-4e53-902a-82e4f3d3e43c)

2] Total number of Bike Trips done by Casual rider and Annual Member by Day of Week in the second half (i.e Between June to December) of the year 2013
![screenshot2](https://github.com/moheenpatel/Cyclistic-bike-share-analysis/assets/72771390/f45c29b8-9b57-4aba-b90a-68d608ca57f2)

3] Average Trip Duration (in mins) taken by Casual rider and Annual Member by Day of Week in the second half (i.e Between June to December) of the year 2013
![screenshot3](https://github.com/moheenpatel/Cyclistic-bike-share-analysis/assets/72771390/11e20929-cd00-4e33-a549-2eb4a936ec78)

### Data Analysis using SQL and Google BigQuery

- Imported data from [Cyclistic_2013_Data.csv](https://drive.google.com/file/d/1vQ8cvs8qzLvy--BICxWY9jqrbYH35Ssm/view?usp=sharing) into table **"cyclistic_2013_data"** present under database **"bike_trip_data"** on Google BigQuery.
![screenshot4](https://github.com/moheenpatel/Cyclistic-bike-share-analysis/assets/72771390/b1e37259-f374-4f28-be4f-e68203c38df4)
![screenshot5](https://github.com/moheenpatel/Cyclistic-bike-share-analysis/assets/72771390/a2bb2b40-dfc4-4fb9-bde5-b0369edf3feb)

- Wrote and Executed below SQL queries to fetch following information :
  
  1] Total number of Bike Trips done by Casual rider and Annual Member by Month in the second half (i.e Between June to December) of the year 2013
```sql
SELECT
    month,
    month_name,
    SUM(CASE WHEN usertype = 'Casual' THEN 1 ELSE 0 END) AS Casual,
    SUM(CASE WHEN usertype = 'Member' THEN 1 ELSE 0 END) AS Member,
    COUNT(*) AS total_trips
FROM
    bike_trip_data.cyclistic_2013_data
WHERE
    usertype IN ('Casual', 'Member')
GROUP BY
    month_name,
    month
ORDER BY
    month;
```
![6](https://github.com/moheenpatel/Cyclistic-bike-share-analysis/assets/72771390/4a4f3efb-92f6-4084-ba99-8b0fdda9c8c3)  

2] Total number of Bike Trips done by Casual rider and Annual Member by Day of Week in the second half (i.e Between June to December) of the year 2013
```sql
SELECT
    weekday,
    day_of_week,
    SUM(CASE WHEN usertype = 'Casual' THEN 1 ELSE 0 END) AS Casual,
    SUM(CASE WHEN usertype = 'Member' THEN 1 ELSE 0 END) AS Member,
    COUNT(*) AS total_trips
FROM
    bike_trip_data.cyclistic_2013_data
WHERE
    usertype IN ('Casual', 'Member')
GROUP BY
    day_of_week,
    weekday
ORDER BY
    weekday;
```
![7](https://github.com/moheenpatel/Cyclistic-bike-share-analysis/assets/72771390/2647a206-8514-4641-abab-1a58ae72974f)

3] Average Trip Duration (in mins) taken by Casual rider and Annual Member by Day of Week in the second half (i.e Between June to December) of the year 2013
```sql
SELECT
    weekday,
    day_of_week,
    AVG(CASE WHEN usertype = 'Casual' THEN tripduration_min END) AS Casual,
    AVG(CASE WHEN usertype = 'Member' THEN tripduration_min END) AS Member
FROM
    bike_trip_data.cyclistic_2013_data
WHERE
    usertype IN ('Casual', 'Member')
GROUP BY
    day_of_week,
    weekday
ORDER BY
    weekday;
```
![8](https://github.com/moheenpatel/Cyclistic-bike-share-analysis/assets/72771390/6e30c1a2-4131-4e8a-ba5e-e7a06b7f5982)

- Saved the Query Results of above 3 SQL queries in below provided CSV files respectively :  
  [total_trips_by_month.csv](https://drive.google.com/file/d/1NM9GQgcslgkEPRKoJOchHaLHQzlxjpqD/view?usp=sharing)  
  [total_trips_by_weekdays.csv](https://drive.google.com/file/d/1jHhexWcjlJpzyjc5RgOJycEkoEpmOMrU/view?usp=sharing)  
  [avg_trip_duration_by_weekdays.csv](https://drive.google.com/file/d/17-pbrjiNZcRAfyMjl9n1I67oO6e5bWrQ/view?usp=sharing)


## Supporting Visualizations and Key Findings

### Data Visualization using Google Sheets / Microsoft Excel  

1] Total number of Bike Trips done by Casual rider and Annual Member by Month in the second half (i.e Between June to December) of the year 2013
![9](https://github.com/moheenpatel/Cyclistic-bike-share-analysis/assets/72771390/354616e8-04e5-480a-a1ef-5da95c84c478)

2] Total number of Bike Trips done by Casual rider and Annual Member by Day of Week in the second half (i.e Between June to December) of the year 2013
![10](https://github.com/moheenpatel/Cyclistic-bike-share-analysis/assets/72771390/5c2a66d0-84a6-4a44-b34e-0c2504e45380)

3] Average Trip Duration (in mins) taken by Casual rider and Annual Member by Day of Week in the second half (i.e Between June to December) of the year 2013
![11](https://github.com/moheenpatel/Cyclistic-bike-share-analysis/assets/72771390/7a2a72c5-5590-4f28-a944-426125857ecd)

### Data Visualization using Tableau

1] Total number of Bike Trips done by Casual rider and Annual Member by Month in the second half (i.e Between June to December) of the year 2013
![total trips by month](https://github.com/moheenpatel/Cyclistic-bike-share-analysis/assets/72771390/e6993538-35c3-4844-be34-81e8e846d7cf)

2] Total number of Bike Trips done by Casual rider and Annual Member by Day of Week in the second half (i.e Between June to December) of the year 2013
![total trips by week](https://github.com/moheenpatel/Cyclistic-bike-share-analysis/assets/72771390/bc6e0bac-d0cc-4aea-8e2b-9aaa409ecabb)

3] Average Trip Duration (in mins) taken by Casual rider and Annual Member by Day of Week in the second half (i.e Between June to December) of the year 2013
![avg trip duration in min by week](https://github.com/moheenpatel/Cyclistic-bike-share-analysis/assets/72771390/8a5306b6-2a26-4fd5-9bb0-5ab6bc0598ca)


### Data Visualization using R

- Imported below 3 CSV files in "Cyclistic bike-share analysis project" on RStudio Cloud (Posit Cloud) :  
  [total_trips_by_month.csv](https://drive.google.com/file/d/1NM9GQgcslgkEPRKoJOchHaLHQzlxjpqD/view?usp=sharing)  
  [total_trips_by_weekdays.csv](https://drive.google.com/file/d/1jHhexWcjlJpzyjc5RgOJycEkoEpmOMrU/view?usp=sharing)  
  [avg_trip_duration_by_weekdays.csv](https://drive.google.com/file/d/17-pbrjiNZcRAfyMjl9n1I67oO6e5bWrQ/view?usp=sharing)
  ![12](https://github.com/moheenpatel/Cyclistic-bike-share-analysis/assets/72771390/1f1189e9-e79b-41b9-b09a-330b52bf07cf)

- Wrote and Executed below R scripts to visualize following information :

  1] Total number of Bike Trips done by Casual rider and Annual Member by Month in the second half (i.e Between June to December) of the year 2013

```r
install.packages("ggplot2")
install.packages("tidyverse")
install.packages("reshape2")

# Load the libraries
library(ggplot2)
library(reshape2)

# Read the CSV file
bike_data <- read.csv("total_trips_by_month.csv")

# Melt the data frame for easier plotting, excluding total_trips
melted_data <- melt(bike_data[, -ncol(bike_data)], id.vars = c("month", "month_name"))

# Reorder the levels of the month_name factor based on the order in the CSV data
melted_data$month_name <- factor(melted_data$month_name, levels = unique(bike_data$month_name))

# Create a line chart for trips by month and user type
ggplot(melted_data, aes(x = month_name, y = value, color = variable, group = variable)) +
  geom_line(size = 1) +
  labs(title = "Total No. of Trips by Month",
       x = "Month",
       y = "Total No. of Trips",
       color = "User Type") +
  theme_minimal()
```

**Result :**  

![13](https://github.com/moheenpatel/Cyclistic-bike-share-analysis/assets/72771390/67579bb4-a56e-47a3-8059-bb81969046db)  



  2] Total number of Bike Trips done by Casual rider and Annual Member by Day of Week in the second half (i.e Between June to December) of the year 2013  

```r
# Install and load necessary libraries
# install.packages(c("ggplot2", "reshape2"))

# Load the libraries
library(ggplot2)
library(reshape2)

# Read the CSV file
total_trips_by_weekdays <- read.csv("total_trips_by_weekdays.csv")

# Melt the data frame for easier plotting, excluding total_trips
melted_data_weekdays <- melt(total_trips_by_weekdays[, -ncol(total_trips_by_weekdays)], id.vars = c("weekday", "day_of_week"))

# Create a line chart for trips by weekday and user type
ggplot(melted_data_weekdays, aes(x = reorder(day_of_week, weekday), y = value, color = variable, group = variable)) +
  geom_line(size = 1) +
  labs(title = "Total No. of Trips by Week",
       x = "Weekday",
       y = "Total No. of Trips",
       color = "User Type") +
  theme_minimal()
```

**Result :**  

![14](https://github.com/moheenpatel/Cyclistic-bike-share-analysis/assets/72771390/4ac494db-b017-4ac8-875e-5049efdcd86d)  


  
  3] Average Trip Duration (in mins) taken by Casual rider and Annual Member by Day of Week in the second half (i.e Between June to December) of the year 2013  

```r
# Read the CSV file
avg_trip_duration_by_weekdays <- read.csv("avg_trip_duration_by_weekdays.csv")

# Melt the data frame for easier plotting, excluding total_trips
melted_data_weekdays <- melt(avg_trip_duration_by_weekdays, id.vars = c("weekday", "day_of_week"))

# Order the melted data based on the order in the CSV file
melted_data_weekdays$day_of_week <- factor(melted_data_weekdays$day_of_week, levels = avg_trip_duration_by_weekdays$day_of_week)

# Create a grouped bar chart for average trip duration by weekday and user type
ggplot(melted_data_weekdays, aes(x = day_of_week, y = value, fill = variable)) +
  geom_bar(stat = "identity", position = "dodge", color = "black") +
  labs(title = "Avg. Trip Duration (in mins) by Weekday",
       x = "Weekday",
       y = "Avg. Trip Duration (in mins)",
       fill = "User Type") +
  theme_minimal()
```

**Result :**  

![15](https://github.com/moheenpatel/Cyclistic-bike-share-analysis/assets/72771390/ae94b86b-fa5f-49cf-affa-57daefd7f2c4)  



### Key Findings from my Data Analysis  

1] Compared to Annual Members, Number of Bike Trips by the Casual Riders increases drastically during the Summer season (i.e June to August) and then decreases drastically as the Winter approaches (i.e September to December).  

2] Number of Bike Trips by the Casual Riders increases drastically during the Weekend (i.e Saturday and Sunday), while during the Weekdays (i.e Monday to Friday) the Number of trips by Casual riders remains very low. On the other hand the trend of Annual members is totally opposite, Number of Bike Trips by the Annual Members remain very low during the Weekend, while during the Weekdays the numbers of bike trips rises and remains almost constant throughout Monday to Friday.  

3] Casual riders go for longer rides than Annual Members.  

4] Above 3 findings suggests that Causual Riders uses the bike-share program only for leisure while the Annual members uses the bike-share program to commute to work each day.  



## My Recommendations based on the Analysis

Below are my few recommendations to the director of marketing for designing marketing strategies aimed at converting casual riders into annual members for company's future growth and success :  

1] Company should introduce Annual Weekend Pass Membership  
2] Company should introduce Summer Membership  
3] Company should make single-ride or full-day passes more costly and Annual Memberships cheaper  



