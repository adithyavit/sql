# sql
### database credits
1. https://github.com/fivethirtyeight/data/tree/master/college-majors
2. dataquest

#### extract first 10 rows from the database jobs.db

#### understanding the data

`select * from recent_grads limit 10`
Header | Description
---|---------
`Rank` | Rank by median earnings
`Major_code` | Major code, FO1DP in ACS PUMS
`Major` | Major description
`Major_category` | Category of major from Carnevale et al
`Total` | Total number of people with major
`Sample_size` | Sample size (unweighted) of full-time, year-round ONLY (used for earnings)
`Men` | Male graduates
`Women` | Female graduates
`ShareWomen` | Women as share of total
`Employed` | Number employed (ESR == 1 or 2)
`Full_time` | Employed 35 hours or more
`Part_time` | Employed less than 35 hours
`Full_time_year_round` | Employed at least 50 weeks (WKW == 1) and at least 35 hours (WKHP >= 35)
`Unemployed` | Number unemployed (ESR == 3)
`Unemployment_rate` | Unemployed / (Unemployed + Employed)
`Median` | Median earnings of full-time, year-round workers
`P25th` | 25th percentile of earnigns
`P75th` | 75th percentile of earnings
`College_jobs` | Number with job requiring a college degree
`Non_college_jobs` | Number with job not requiring a college degree
`Low_wage_jobs` | Number in low-wage service jobs


#### SQL query that returns the majors where females were a minority

`select Major, ShareWomen from recent_grads
 where ShareWomen < 0.5`

#### SQL query that returns:
##### All majors with majority female and
##### All majors had a median salary greater than 50000.

`select Major, Major_category, Median, ShareWomen from recent_grads
where ShareWomen >0.5 and Median > 50000`


#### SQL query that returns the first 20 majors that either:
##### Have a Median salary greater than or equal to 10,000, or
##### Have less than or equal to 1,000 Unemployed people
`select Major, Median, Unemployed from recent_grads
where Median>=10000 or Unemployed <= 1000
limit 20`

#### uery we explored above, which returns all majors that:
##### Fell under the category of Engineering and either
##### Had mostly women graduates
##### Or had an unemployment rate below 5.1%, which was the rate in August 2015

`SELECT Major, Major_category, ShareWomen, Unemployment_rate
from recent_grads
where Major_category="Engineering" and (ShareWomen > 0.5 or Unemployment_rate <0.051)`
