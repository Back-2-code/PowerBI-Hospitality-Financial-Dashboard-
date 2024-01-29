# Hospitality Financial Analysis

![page 2](https://github.com/Back-2-code/PowerBI-Hospitality-Financial-Dashboard-/assets/97646657/334e7f03-b027-43a7-9dc2-37de2f1b5dd6)
## Table of Contents
- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Scope of the project](#scope-of-the-project)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Analysis](#data-analysis)
- [Results and Findings](#results-and-findings)
- [Recommendations](#recommendations)
- [Limitations](#limitations)

### Project Overview
This data analysis project aims to provide insights into the revenue and performance of a hospitality company over the last quarter. The company has multiple hotels spread all across the country. By analyzing various aspects of the sales data, we seek to identify trends, gain a deeper understanding of the company's performance, and help the regional manager in making data-driven decisions.

### Data Sources
The data was used from the below csv files
1. dim_date
2. dim_hotels
3. dim_rooms
4. fact_aggregated_bookings
5. fact_bookings


### Scope of the project

- Data Cleaning In the initial data preparation phase, we performed the following tasks:
  - Data loading and inspection
  - Handling missing values.
  - Data cleaning and formatting.
- Modeling
- Data transformation
- DAX
- Creating Report and Dashboard

### Exploratory Data Analysis

EDA involved exploring the sales data to answer key questions, such as:

- What is the overall RevPar trend?
- Which hotels are performing the best?
- What are the peak booking periods?

### Data Analysis

Some common terms for the hospitality industry that would be required to perform the analysis -

Friday and Saturday is considered as the weekend days. Total available rooms are not always equal to total number of rooms in a hotel. The rooms may require maintenance (plumbing, electrical etc) which reduces total available rooms.  

Total available rooms are also known as DSRN - Daily Sellable Room Nights.
RevPar - Revenue per available room  => Revenue / Total available room or it can also be calculated as ADR x Occupancy
ADR - Average Daily Rate => Total Revenue/Number of Rooms sold
Occupancy % - Total occupied rooms / Total available rooms
URN - Utilised Room Nights or actual rooms booked
BRN - Booked Room Nights + no show + cancellation
Realization % = URN / BRN


```dax
Revenue WoW change % = 
Var selv = IF(HASONEFILTER(dim_date[wn]),SELECTEDVALUE(dim_date[wn]),MAX(dim_date[wn]))
var revcw = CALCULATE([Revenue],dim_date[wn]= selv)
var revpw =  CALCULATE([Revenue],FILTER(ALL(dim_date),dim_date[wn]= selv-1))

return DIVIDE(revcw,revpw,0)-1
```

### Results and Findings

The analysis results are summarized as follows:
1. Demand changes significantly from weekdays to weekends  
2. The company's revenue has been steadily increasing over the past quarter, as the holiday season is approaching.
3. Revenue has stayed constant for some hotels even though the occupancy was at its peak.
4. Customer segments with high lifetime value (LTV) should be targeted for marketing efforts.

![image](https://github.com/Back-2-code/PowerBI-Hospitality-Financial-Dashboard-/assets/97646657/b664e9da-30fa-44ca-9eed-c3d8ae0f54de)


### Recommendations

Based on the analysis, we recommend the following actions:
- Weekly pricing of the rooms should be adopted to maximize revenue for weekend bookings.
- Invest in marketing, promotions, and reputation on booking platforms to improve occupancy in low-performing hotel.
- Dynamic strategic pricing before the holiday season to account for seasonal change.
