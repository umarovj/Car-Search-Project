# Car-Search-Project
My independent project to help me research the current auto market
## Summary
I have recently heard the news that the auto market is starting to significatnly change post pandemic years. Meanwhile my current car was getting old and I started to explore the idea of buying a new one. I noticed more and more youtube videos like this (https://www.youtube.com/watch?v=zhmr8w-A7YQ) explaining that the car market got inflated during the COVID 19 pandemic and will soon pop. As a data analyst I couldnt take youtubers' word without seting my own research and analytics. Therefore I compiled thousands of auto listings from Cars.com and tracked the prices over time. 

I created a scraping script in Python Pandas using the BeautifulSoup package. This code scrapped roughly five thousand aut listings in my area (Minneapolis). I scapped infomration such as the make, model, VIN number, and much more in case I would like to test other hypothesies. I reran my code couple times a week and labeled the results by date. Then I imported this information into PostgresSQL local database to find price differences. 

## Python Code

I used the auto listings website Cars.com as the source for my data. In order to scrape the data from this website I used the BeautifulSoup package. While on the site, I set my search filters local to my zip code within 100 mile radius then copied the URL for BeautifulSoup. 

I set up my Columns and scraped these parameters of over five thousand Cars.com listings:

- 'Year'
- 'Make'
- 'Model'
- 'Used_or_New'
- 'Price'
- 'ConsumerRating'
- 'ConsumerReviews'
- 'SellerType'
- 'SellerName'
- 'SellerRating'
- 'SellerReviews'
- 'StreetName'
- 'State'
- 'Zipcode'
- 'DealType'
- 'ComfortRating'
- 'InteriorDesignRating'
- 'PerformanceRating'
- 'ValueForMoneyRating'
- 'ExteriorStylingRating'
- 'ReliabilityRating'
- 'ExteriorColor'
- 'InteriorColor'
- 'Drivetrain'
- 'MinMPG'
- 'MaxMPG'
- 'FuelType'

           'Transmission','Engine','VIN','Stock','Mileage'] 





## SQL Query
The images below represent the query I ran to extract price differences. 


After converting the data into a CSV file, I imported the data into a PostgreSQL database. The VIN number was used to uniquely identify vehicles with future listings.

I applied the following query to check for duplicate VIN numbers and delete repeated ones:

![image 1](https://github.com/umarovj/Car-Search-Project/blob/main/Query%20Results/SQL%20duplicate%20check.png)

Then I created a query to look at the price difference and price difference by percentage between said dates:

![image 2](https://github.com/umarovj/Car-Search-Project/blob/main/Query%20Results/SQL%20price%20diff%20as%20percentage.png)










