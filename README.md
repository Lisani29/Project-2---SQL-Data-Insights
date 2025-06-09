# Project-2---SQL-Data-Insights
This project showcases hands-on SQL analysis using public datasets in **Google BigQuery**. 
It includes insights derived from large real-world datasets like **US Baby Names**, **COVID-19 Data**, and **311 Service Requests in New York**.

---

##  Tools & Platform
- Google BigQuery (cloud-based SQL)
- SQL (Structured Query Language)
- Public Datasets from Google Cloud
---

## Datasets Used

1. **US Baby Names**  
   Source: `bigquery-public-data.usa_names.usa_1910_2013`

2. **COVID-19 Open Data**  
   Source: `bigquery-public-data.covid19_open_data.covid19_open_data`

3. **NYC 311 Complaints**  
   Source: `bigquery-public-data.new_york.311_service_requests`

---

## Key Insights
###  1. Most Popular Baby Names in California
```sql
SELECT name, gender, SUM(number) as total
FROM `bigquery-public-data.usa_names.usa_1910_2013`
WHERE state = 'CA'
GROUP BY name, gender
ORDER BY total DESC
LIMIT 10;

**Insight:** The name James was the most common male name in California, followed by John and Robert. For females, Mary was most popular.

**###  2. COVID-19 Deaths by Country (June 2021)**

SELECT country_name, SUM(cumulative_deceased) AS total_deaths
FROM `bigquery-public-data.covid19_open_data.covid19_open_data`
WHERE date = '2021-06-01'
GROUP BY country_name
ORDER BY total_deaths DESC
LIMIT 10;

**Insight:** As of June 2021, USA, Brazil, and India had the highest number of reported COVID-19-related deaths.

**###  3.  Most Frequent Complaints in NYC**

SELECT complaint_type, COUNT(*) AS total_complaints
FROM `bigquery-public-data.new_york.311_service_requests`
GROUP BY complaint_type
ORDER BY total_complaints DESC
LIMIT 10;

**Insight:** Noise - Residential and Illegal Parking were among the most common citizen complaints in New York City.

