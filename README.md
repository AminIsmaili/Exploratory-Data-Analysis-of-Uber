# Exploratory-Data-Analysis-of-Uber


**Objective**:
To analyze key factors affecting ride-sharing demand, pricing, and trip distances for Uber and Lyft, identifying patterns that influence fare strategies, peak demand, and operational efficiency.

**Problem Statement**:
Ride-sharing companies like Uber and Lyft face challenges in demand forecasting, fare optimization, and operational efficiency due to fluctuating factors such as seasonality, pricing models, and weather conditions. Without a clear understanding of these variables, companies may struggle with pricing inconsistencies, supply-demand mismatches, and reduced profitability. This study aims to analyze historical ride data to identify key trends, correlations, and insights that can help enhance pricing strategies, optimize resource allocation, and improve user experience.

Following are the questions considered for profound analaysis. 

**Price/Fare Analysis**:

1. Calculate the average fare of Uber and Lyft rides

2. Analyze the distribution of fares

3. What is the overall price per kilometer?

4. Price per km of Uber and Lyft separately

5. What revenue is generated on a monthly basis?

6. What are the revenue patterns by days?

7. Examine the correlation between distance and fare to understand pricing dynamics

8. What is the average fare variation by weather?

**Distance Analysis**:

9. What is the average trip distance for Uber and Lyft?

10. Total distance covered by each cab type

11. What is the distribution of trip distances to identify common trip lengths?

12. What are the longest and shortest trips by each cab service?

**Ride Volume & Seasonal Trends**:

13. What are the total rides on a monthly basis?

14. Which cab rides peaked in certain months?

15. On which days of the week do rides normally surge?

16. Which day had a significant drop in rides?

17. Find the most popular pickup destinations for each cab type.

18. Find the least popular pickup destinations for each cab type.

**Weather & Temperature Impact**:

19. Assess how different weather conditions (temperature) affect ride pricing.

20. Assess how different weather conditions (temperature) affect ride frequency.

21. What is the impact of different weather conditions on overall ride patterns?

**Methodolgy:**

**1. Data Cleaning & Processing Steps**:

  - **Data Type Conversion**: The datetime column was converted to the correct datetime data type using pd.to_datetime.

  - **Irrelevant Column Removal**: Redundant or irrelevant columns, like id, timestamp, timezone, etc., were removed using the df.drop method.

  - **Missing Value Handling**:
Missing values in the price column were dropped since they represented less than 10% of the data. This was done using df.dropna(subset=["price"]).

  - **Column Renaming**:
Column names were made more descriptive and units were added (e.g., 'price' became 'price($)' and 'distance' became 'distance(km)'). This improves readability and understanding.

  - **Feature Engineering**:
New features like date, time, month, day, and hour were extracted from the datetime column to facilitate further analysis. These features can provide valuable insights into temporal patterns in the data.

**2. Data Description**:

  - **Descriptive Statistics**: The df.describe().transpose() function was used to generate descriptive statistics (like mean, standard deviation, min, max, quartiles) for numerical columns. These statistics provide a basic understanding of the data distribution and central tendencies.

  - **Correlation Analysis**:
A correlation matrix (df.corr()) and a heatmap were used to explore relationships between numerical features. This analysis helps identify potential dependencies or redundancies among variables.

  - **Distribution Analysis, Skewness and Outlier Remova**l: 

  - **Distribution Analysis**: Histograms were generated to visualize the distributions of key numerical features, such as price, distance, and surge_multiplier. This visual inspection helps identify potential skewness or outliers.

  - **Skewness Analysis**: The skewness of each numerical feature was calculated using the skew() method. Features with skewness values outside the range of -1 to 1 were identified as having skewed distributions.

  - **Outlier Removal**: Outliers were identified and removed using the Interquartile Range (IQR) method. This involved calculating the IQR, setting lower and upper bounds, and removing data points falling outside these bounds. This method helps ensure that extreme values do not unduly influence the analysis.

**Key Insights from EDA**:

1.	Lyft holds a slight market share advantage over Uber (51% vs 49%), indicating a potentially larger user base for Lyft.
2.	Uber's average fares are slightly lower than Lyft's ($16.45 vs 15.53), 
3.	Lyft has higher price per kilometer than Uber ($7.60 vs $7.37). This suggests Uber might be focusing on attracting price-sensitive customers or strategically adjusting pricing to optimize profits.
4.	November generated higher revenue ($2,581,141.7) and more rides (161,767) compared to December ($2,385,263 and 149,274 rides), indicating a possible seasonal decline in ride demand
5.	Friday generated the highest revenue ($1,022,380.85), while Tuesday had the lowest ($441,359.00), indicating higher ride demand towards the weekend. Midweek revenue remains moderate, with a slight increase on Wednesday ($879,326.85)
6.	Lyft has a slightly higher average trip distance (2.16 km) than Uber (2.11 km), indicating longer rides on average.
7.	Total distance covered is also higher for Lyft (7.60 million km) compared to Uber (7.36 million km).
8.	The correlation between distance and fare is 0.32, suggesting a weak positive relationship—longer trips slightly increase fares but are not the only pricing factor.
9.	The shortest and longest trips for Lyft range from 0.39 km to 5.42 km, while for Uber, trips vary between 0.02 km and 5.16 km. This suggests that Uber accommodates slightly shorter trips than Lyft, while Lyft handles marginally longer maximum trips.
10.	For Lyft, the most popular pickup location is Haymarket Square (12,996 rides), while for Uber, it is South Station (14,210 rides), indicating high demand in central transit areas. The least popular pickup location for Lyft is Back Bay (11,342 rides), and for Uber, it is Financial District (11,953 rides), suggesting relatively lower ride activity in these areas.
11.	Cab rides peaked in November, with Uber (85,881 rides) and Lyft (75,886 rides) experiencing the highest demand, while December saw a slight decline. Fridays have the highest ride demand, with Uber (33,979 rides) and Lyft (30,282 rides), likely due to increased weekend travel. Rides drop significantly on Mondays and Tuesdays, with the lowest demand seen on Tuesdays (Uber: 14,631, Lyft: 13,030), suggesting reduced weekday commuting activity.
12.	Ride prices remain relatively stable across both high and low temperatures, with only minor fluctuations. Higher temperatures (45–49°F) show fares ranging from $15.58 to $16.09, while lower temperatures (27–28°F) have slightly higher fares, reaching up to $16.40. This suggests that colder weather may lead to slightly increased pricing, possibly due to higher demand or challenging driving conditions
13.	Overcast weather has the highest ride volume (113,134 rides), while drizzle conditions see the lowest (1,478 rides), indicating that cloudy conditions do not significantly reduce demand. 


**Reccomendations**:

**1. Optimize Pricing Strategies for Demand Peaks & Lows:**

- Continue leveraging competitive pricing to attract price-sensitive customers.
- Introduce dynamic pricing or promotions on low-demand days (Monday & Tuesday) to balance weekly ride distribution.

**2. Maximize Short-Distance Ride Turnover:**

- Since Uber handles shorter trips more efficiently, optimize driver allocation in areas with frequent short rides (e.g., city centers).
- Introduce incentives for drivers to stay in high-demand zones like South Station to reduce wait times.

**3. Leverage Seasonal Demand Fluctuations:**

- Since November had the highest demand, plan marketing campaigns and surge pricing adjustments for peak travel months.
- Offer discounted or bundled rides in December to counter the slight drop in demand.

**4. Use Weather-Based Surge Pricing & Demand Forecasting:**

- Implement slight fare adjustments during colder weather when demand rises slightly.
- Ensure sufficient driver availability in overcast conditions, where ride volume remains high.

**5. Expand Market Presence in Low-Demand Areas:**

- Financial District has lower ride volume; Uber can introduce targeted promotions or partnerships to increase demand.
- Increase advertising in low-demand locations (like the Financial District) to encourage more ride bookings.
