# Car-Search-Project
My independent project to help me research the current auto market
## Summary
I have recently heard the news that the auto market is starting to significatnly change post pandemic years. Meanwhile my current car was getting old and I started to explore the idea of buying a new one. I noticed more and more youtube videos like this (https://www.youtube.com/watch?v=zhmr8w-A7YQ) explaining that the car market got inflated during the COVID 19 pandemic and will soon pop. As a data analyst I couldnt take youtubers' word without seting my own research and analytics. Therefore I compiled thousands of auto listings from Cars.com and tracked the prices over time. 

I created a scraping script in Python Pandas using the BeautifulSoup package. This code scrapped roughly five thousand aut listings in my area (Minneapolis). I scapped infomration such as the make, model, VIN number, and much more in case I would like to test other hypothesies. I reran my code couple times a week and labeled the results by date. Then I imported this information into PostgresSQL local database to find price differences. 


## SQL Query
The images below represent the query I ran to extract price differences. 


After converting the data into a CSV file, I imported the data into a PostgreSQL database. The VIN number was used to uniquely identify vehicles with future listings. 
