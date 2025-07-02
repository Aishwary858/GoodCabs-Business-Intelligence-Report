# GoodCabs-Business-Intelligence-Report

## Problem Statement
Domain: Transportation & Mobility

Goodcabs, a cab service company established two years ago, has gained a strong foothold in the Indian market by focusing on tier-2 cities. Unlike other cab service providers, Goodcabs is committed to supporting local drivers, helping them make a sustainable living in their hometowns while ensuring excellent service to passengers. With operations in ten tier-2 cities across India, Goodcabs has set ambitious performance targets for 2024 to drive growth and improve passenger satisfaction.

As part of this initiative, the Goodcabs management team aims to assess the company's performance across key metrics, including trip volume, passenger satisfaction, repeat passenger rate, trip distribution, and the balance between new and repeat passengers.


### Steps followed 
- Step 1 : Downloaded CSV datasets from web sources containing.
- Step 2 : Load data into Power BI Desktop, dataset is a csv file.
- Step 3 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.
- Step 4 : Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".
- Step 5 : It was observed that in none of the columns errors & empty values were present , In "monthly_target_new_passengers" table i use First row as header .
- Step 6 : Data Modeling in Modeling Tab Switched to Modeling tab to create relationships.
- Step 7 : DAX Measures Creation .
- Step 8 : Applied custom theme with GOODCABS branding colors (green/blue palette).
- Step 9 : Visual Creation & KPI Cards.
- Step 10: Interactive Filters (Slicers) For City , Month and  Passenger Type .
  
### Create one measure table and add some important measure for Analysis
1.Avg Driver Rating = AVERAGE(fact_trips[driver_rating])

2.Avg Fare Per Km = DIVIDE([Total Fare(Revenue)],[Total Distance Travelled],0)

3.Avg Fare Per Trip = DIVIDE([Total Fare(Revenue)],[Total Trips],0)

4.Avg Passenger Rating = AVERAGE(fact_trips[passenger_rating])

5.Avg Passenger Rating Target = AVERAGE(city_target_passenger_rating[target_avg_passenger_rating])

6.Avg Trip Distance = AVERAGE(fact_trips[distance_travelled(km)])

7.New Passengers = SUM(fact_passenger_summary[new_passengers])

8.New Passengers Actual vs New Passengers Target = DIVIDE([New Passengers]-[New Target Passengers],[New Target Passengers],0)

9.New Target Passengers = SUM(monthly_target_new_passengers[target_new_passengers])

10.New Trips = CALCULATE([Total Trips],fact_trips[passenger_type]="new")

11.New vs Repeated Passengers Trip Ratio = DIVIDE([New Trips],[Repeated Trips],0)

12.Repeat Passenger Count = SUM(dim_repeat_trip_distribution[repeat_passenger_count])

13.Repeat Passenger Rate % = DIVIDE([Repeated Passengers],[Total Passengers],0)

14.Repeated Passengers = SUM(fact_passenger_summary[repeat_passengers])

15.Repeated Trips = CALCULATE([Total Trips],fact_trips[passenger_type]="repeated")

16.Total Distance Travelled = SUM(fact_trips[distance_travelled(km)])

17.Total Fare(Revenue) = SUM(fact_trips[fare_amount])

18.Total Passengers = SUM(fact_passenger_summary[total_passengers])

19.Total Trips = DISTINCTCOUNTNOBLANK(fact_trips[trip_id])

20.Trips Actual vs Trips Target = DIVIDE([Total Trips]-[Trips Target],[Trips Target],0)

21.Trips Target = SUM(monthly_target_trips[total_target_trips])

 
 # Report Snapshot (🏠Home Page)

 
![Image](https://github.com/user-attachments/assets/1ff2bcc1-363c-4495-a492-77898e994d60)





 # Report Snapshot (🚕Overview Page)

 ![Image](https://github.com/user-attachments/assets/07040739-71fb-496c-97e8-c9297ee97c19)

##  📊 Page Overview
The Overview Page serves as the central command center of the GOODCABS report, providing comprehensive business metrics and operational insights at a glance. This page enables stakeholders to quickly assess overall business performance and identify key trends.

### 📈 Key Performance Indicators (KPIs)
1.426K Total Trips- Goodcabs completed 426,000 rides in total.

2.₹108M Total Fare - Goodcabs earned 108 million rupees from all rides. 

3.8M Total Distance Travelled- All their taxis together traveled 8 million kilometers. 

4.₹13.28 Average Fare Per Km- On average, passengers pay ₹13.28 for each kilometer. 

5.₹254.02 Average Fare Per Trip- Each ride costs about ₹254 on average.

6.19.13 Average Trip Distance- Each ride covers about 19 kilometers on average. 

 

### Insights
- Jaipur is doing 5 times better than Coimbatore! Some cities are much more successful.
- More than half the trips come from people who used Goodcabs before - that's great for business.
- Different cities have different ride patterns.

# Report Snapshot (🎯Target and Ratings Page)

![Image](https://github.com/user-attachments/assets/502912c9-4553-4592-8165-2113761a7171)


##  📊 Target and Ratings
The Targets and Ratings Page serves as the performance monitoring hub of the GOODCABS report, focusing on goal achievement tracking, customer satisfaction metrics, and service quality analysis. This page enables management to assess performance against targets and monitor service excellence.

### 📈 Key Performance Indicators (KPIs)
1.	238K Total Passengers- 238,000 different people used Goodcabs.
2.	177K New Trips- 177,000 trips were taken by first-time users.
3.	249K Repeated Trips- 249,000 trips were taken by returning customers.

### Insights
1.Best Performance: February (+4.2% trips target achieved).
2.Mixed performance - some months great, others struggled.
3.Surat: 42.63% repeat rate (Excellent loyalty).
4.Lucknow: 37.12% repeat rate (Strong loyalty).




# Report Snapshot (🌆City Performance Page)

![Image](https://github.com/user-attachments/assets/069ff02e-045c-4a58-82ab-791541782a79)

##  📊 City Performance
The City Performance Page serves as the geographic intelligence center of the GOODCABS report, providing detailed city-wise analysis, revenue optimization insights, and market performance comparisons. This page enables regional managers to assess individual city performance and identify growth opportunities.

### 📈 Key Performance Indicators (KPIs)
1.Average Passenger Rating - Customer satisfaction score

2.Average Trip Distance - Mean distance per trip

### Insights
1.Jaipur and Kochi dominate - they each make about 4x more than the smallest cities.

2.Big gap between top and bottom - Jaipur makes ₹17M vs Coimbatore's ₹4M.

3.Jaipur: 28km distance, ₹500+ revenue per trip.

4.Jaipur Dominance: 34.3% market share, clear leader.

5.Growth Markets: Kochi, Chandigarh showing strong potential.




#  Conclusion 
1.426K trips were completed, and the company generated a total revenue of ₹108M across 10 cities.

2.The total distance traveled is 8 million km, with an average fare per km of ₹13.28 and average fare per trip of ₹254.

3.Each ride covers an average distance of 19.13 km, indicating mid- to long-distance urban trips.

4.repeat users making up the majority of trips. 



# Suggestions
1.Focus on improving performance in bottom cities like 
Coimbatore and Mysore — consider promotions or quality upgrades.

2.Strengthen customer loyalty in cities with low repeat rates (e.g., Jaipur) by introducing reward programs. 

3.Maintain high passenger and driver ratings by monitoring service quality. 






  

           

