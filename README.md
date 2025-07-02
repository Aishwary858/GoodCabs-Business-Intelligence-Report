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
  
Create one measure table and add some important measure for Analysis
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


        


        
- Step 15 : New measure was created to find total count of customers.

Following DAX expression was written for the same,
        
        Count of Customers = COUNT(airline_passenger_satisfaction[ID])
        
A card visual was used to represent count of customers.

![Snap_Count](https://user-images.githubusercontent.com/102996550/174090154-424dc1a4-3ff7-41f8-9617-17a2fb205825.jpg)

        
 - Step 16 : New measure was created to find  % of customers,
 
 Following DAX expression was written to find % of customers,
 
         % Customers = (DIVIDE(airline_passenger_satisfaction[Count of Customers], 129880)*100)
 
 A card visual was used to represent this perecntage.
 
 Snap of % of customers who preferred business class
 
 ![Snap_Percentage](https://user-images.githubusercontent.com/102996550/174090653-da02feb4-4775-4a95-affb-a211ca985d07.jpg)

 
 - Step 17 : New measure was created to calculate total distance travelled by flights & a card visual was used to represent total distance.
 
 Following DAX expression was written to find total distance,
 
         Total Distance Travelled = SUM(airline_passenger_satisfaction[Flight Distance])
    
 A card visual was used to represent this total distance.
 
 
 ![Snap_3](https://user-images.githubusercontent.com/102996550/174091618-bf770d6c-34c6-44d4-9f5e-49583a6d5f68.jpg)
 
 - Step 18 : The report was then published to Power BI Service.
 
 
![Publish_Message](https://user-images.githubusercontent.com/102996550/174094520-3a845196-97e6-4d44-8760-34a64abc3e77.jpg)

# Snapshot of Dashboard (Power BI Service)

![dashboard_snapo](https://user-images.githubusercontent.com/102996550/174096257-11f1aae5-203d-44fc-bfca-25d37faf3237.jpg)

 
 # Report Snapshot (Power BI DESKTOP)

 
![Dashboard_upload](https://user-images.githubusercontent.com/102996550/174074051-4f08287a-0568-4fdf-8ac9-6762e0d8fa94.jpg)

# Insights

A single page report was created on Power BI Desktop & it was then published to Power BI Service.

Following inferences can be drawn from the dashboard;

### [1] Total Number of Customers = 129880

   Number of satisfied Customers (Male) = 28159 (21.68 %)

   Number of satisfied Customers (Female) = 28269 (21.76 %)

   Number of neutral/unsatisfied customers (Male) = 35822 (27.58 %)

   Number of neutral/unsatisfied customers (Female) = 37630 (28.97 %)


           thus, higher number of customers are neutral/unsatisfied.
           
### [2] Average Ratings

    a) Baggage Handling - 3.63/5
    b) Check-in Service - 3.31/5
    c) Cleanliness - 3.29/5
    d) Ease of online booking - 2.88/5
    e) Food & Drink - 3.21/5
    f) In-flight Entertainment - 3.36/5
    g) In-flight service - 3.64/5
    h) In-flight Wifi service - 2.81/5
    i) Leg room service - 3.37/5
    j) On-board service - 3.38/5
    k) Online boarding - 3.33/5
    l) Seat comfort - 3.44/5
    m) Departure & arrival convenience - 3.22/5
  
  while calculating average rating, null values have been ignored as they were not relevant for some customers. 
  
  These ratings will change if different visual filters will be applied.  
  
  ### [3] Average Delay 
  
      a) Average delay in arrival(minutes) - 15.09
      b) Average delay in departure(minutes) - 14.71
Average delay will change if different visual filters will be applied.

 ### [4] Some other insights
 
 ### Class
 
 1.1) 47.87 % customers travelled by Business class.
 
 1.2) 44.89 % customers travelled by Economy class.
 
 1.3) 7.25 % customers travelled by Economy plus class.
 
         thus, maximum customers travelled by Business class.
 
 ### Age Group
 
 2.1)  21.69 % customers belong to '0-25' age group.
 
 2.2)  52.44 % customers belong to '25-50' age group.
 
 2.3)  25.57 % customers belong to '50-75' age group.
 
 2.4)  0.31 % customers belong to '75-100' age group.
 
         thus, maximum customers belong to '25-50' age group.
         
### Customer Type

3.1) 18.31 % customers have customer type 'First time'.

3.2) 81.69 % customers have customer type 'returning'.
       
       thus, more customers have customer type 'returning'.

### Type of travel

4.1) 69.06 % customers have travel type 'Business'.

4.2) 30.94 % customers have travel type 'Personal'.

        thus, more customers have travel type 'Business'.
