# Hospitality Financial Analysis

#Table of Contents
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

```dax
Revenue WoW change % = 
Var selv = IF(HASONEFILTER(dim_date[wn]),SELECTEDVALUE(dim_date[wn]),MAX(dim_date[wn]))
var revcw = CALCULATE([Revenue],dim_date[wn]= selv)
var revpw =  CALCULATE([Revenue],FILTER(ALL(dim_date),dim_date[wn]= selv-1))

return DIVIDE(revcw,revpw,0)-1
```

### Results and Findings

The analysis results are summarized as follows:
1. The company's sales have been steadily increasing over the past year, with a noticeable peak during the holiday season.
2. Product Category A is the best-performing category in terms of sales and revenue.
3. Customer segments with high lifetime value (LTV) should be targeted for marketing efforts.

### Recommendations

Based on the analysis, we recommend the following actions:
- Invest in marketing and promotions during peak sales seasons to maximize revenue.
- Focus on expanding and promoting products in Category A.
- Implement a customer segmentation strategy to target high-LTV customers effectively.

### Limitations

I had to remove all zero values from budget and revenue columns because they would have affected the accuracy of my conclusions from the analysis. There are still a few outliers even after the omissions but even then we can still see that there is a positive correlation between both budget and number of votes with revenue.
