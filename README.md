# Car-Search-Project
My independent project to help me research the current auto market
## Summary
I have recently heard the news that the auto market is starting to significatnly change post pandemic years. Meanwhile my current car was getting old and I started to explore the idea of buying a new one. I noticed more and more youtube videos like this (https://www.youtube.com/watch?v=zhmr8w-A7YQ) explaining that the car market got inflated during the COVID 19 pandemic and will soon pop. As a data analyst I couldnt take youtubers' word without seting my own research and analytics. Therefore I compiled thousands of auto listings from Cars.com and tracked the prices over time. 

I created a scraping script in Python Pandas using the BeautifulSoup package. This code scrapped roughly five thousand aut listings in my area (Minneapolis). I scapped infomration such as the make, model, VIN number, and much more in case I would like to test other hypothesies. I reran my code couple times a week and labeled the results by date. Then I imported this information into PostgresSQL local database to find price differences. 

## Python Code

I used the auto listings website Cars.com as the source for my data. In order to scrape the data from this website I used the BeautifulSoup package. While on the site, I set my search filters local to my zip code within 100 mile radius then copied the URL for BeautifulSoup. 

I set up my Variables and scraped over five thousand Cars.com listings:

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
- 'Transmission'
- 'Engine'
- 'VIN'
- 'Stock'
- 'Mileage' 

The raw values provided in the website would not apply when importing into PostgreSQL. I needed to clean my data. 

Firstly I delete two columns, 'interiorcolor' and 'exteriorcolor', because they contained special characters that made it harder for PostgreSQL to read. In addition, these values did not bring any use for my project.

![image P1](https://github.com/umarovj/Car-Search-Project/blob/main/Images/Drop%20columns.png)

I noticed that I had 'Not Priced' values under my 'Price' column which should all be integers. This will cause importing error in PostgreSQL, therefore I replaced all of these values to NaN with this code:

![image P2](https://github.com/umarovj/Car-Search-Project/blob/main/Images/replace%20not%20priced.png)

I was not done fixing this column. The prices still showed '$' and ',' characters which would still cause an importing error. This code cleans will eliminate those characters:

![image P3](https://github.com/umarovj/Car-Search-Project/blob/main/Images/remove%20signs%20from%20price.png)

Now I am ready to export the data into a csv file using this code: 

![image P4](https://github.com/umarovj/Car-Search-Project/blob/main/Images/export%20to%20csv.png)


## SQL Query
The images below represent the query I ran to extract price differences. 


After converting the data into a CSV file, I imported the data into a PostgreSQL database. The VIN number was used to uniquely identify vehicles with future listings.

I applied the following query to check for duplicate VIN numbers and delete repeated ones:

![image 1](https://github.com/umarovj/Car-Search-Project/blob/main/Images/SQL%20duplicate%20check.png)

Then I created a query to look at the price difference and price difference by percentage between said dates:

![image 2](https://github.com/umarovj/Car-Search-Project/blob/main/Images/SQL%20price%20diff%20as%20percentage.png)

I collected this data over a course of a month and imported them into Tableau to visualize the results. 

## Data Insights

Using Tabeau, I gather all the data show general overview and instersting insights. I wanted to know which cars are being sold the most in my area. Out of a sample pool of five thousand listntings near my area here is what I created:

![image 3](https://github.com/umarovj/Car-Search-Project/blob/main/Images/Dashboard%201.png)

The first Graphic shows the most common car brands listed in ascending order. I found that Ford is the most common with 154 listings and Honda is second with 121 listings. 

The second graphic underneath shows the most common models of these brands. This shows that Chevrolet Equinox is the most common car sold with 39 listings and Ford f-150 is the second more common with 37 listings. These graphics do no represent the entire pool and less common brands or models have been conditionally excluded out of view. 

I also wondered about who are the sellers that post the most on Cars.com. This graphic below represent the most common sellers out of five thousand listings with proportion of each car brand sold. 

![image 4](https://github.com/umarovj/Car-Search-Project/blob/main/Images/Which%20Dealers%20Are%20Listing%20The%20Most_.png)

Apperently Buerkly Hyundai listed the most with 50 listings. What is interesting is that this seller listed more Hondas than Hyundais.

It was also interesting to view where in my region cars are being sold the most. Therefore I matched the zip codes to the mapping feature in tableau and created this graphic below:



## Results












