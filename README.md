# Big Mountain Resort Pricing Model

<img width="1060" alt="Screenshot 2024-06-30 at 2 41 25 PM" src="https://github.com/aliakdeniz38/DataScienceGuidedCapstone/assets/44283034/4a723c28-86e9-470c-9c9b-b87d91308c64">

## Problem Statement:    
By leveraging data analytics to understand visitor patterns and facility usage, Big Mountain Resort will implement a new pricing strategy and operational improvements that will result in a 15% increase in ticket revenue, a 10% improvement in visitor satisfaction scores, and a 5% reduction in operating costs within the next winter season.

## Context:
Big Mountain Resort suspects they are not maximizing the potential of their facilities. The pricing strategy based solely on market averages does not accurately reflect the value of their facilities, which impacts their investment strategy. They need a data-driven approach to determine the optimal ticket price and identify cost-saving measures without reducing ticket prices.

## Criteria for success:
**Revenue Increase:** Achieve a measurable increase in ticket revenue within the first season after implementing the new pricing strategy.
**Cost Efficiency:** Identify and implement cost-saving measures that do not negatively impact the visitor experience, with a target reduction in operating costs.

## Scope of solution space:
**Data Analysis:** Conduct comprehensive analysis of visitor patterns, facility usage, and pricing models using the provided dataset.
**Pricing Model:** Develop and test different pricing models based on facility value and visitor preferences.
**Operational Efficiency:** Identify areas for operational cost reduction without diminishing service quality.
**Implementation Plan:** Create a detailed implementation plan for the new pricing strategy and operational changes.

## Constraints within solution space:
**Data Limitations:** The analysis is limited to the data provided by the resort. Additional data sources may be required for a more comprehensive analysis.
**Operational Resistance:** Changes in pricing or operations may face resistance from stakeholders or visitors.
**Seasonal Variability:** Visitor patterns and revenue can vary significantly by season, impacting the generalizability of findings.

## Stakeholders to provide key insight:
**Director of Operations:** Jimmy Blackburn
**Database Manager:** Alesha Eisen
**Other Stakeholders:** Resort management, financial team, marketing team, and visitors.

## Key data sources: 
**Primary Source:** CSV file provided by Alesha Eisen, containing data from 330 resorts in the US, including Big Mountain Resort.

## Feature Engineering:
 * **Feature Correlation heatmap**: a great way to gain a high level view and idnetify patterns of relationships amongst the features:
     * summit and base elevation are quite highly correlated. This isn't a surprise. 
     * AdultWeekend ticket price, we see quite a few reasonable correlations. fastQuads stands out, along with Runs and Snow Making_ac. 
     * The last one is interesting. Visitors would seem to value more guaranteed snow, which would cost in terms of snow making equipment, which would drive prices and costs up.
     * As well as Runs, total_chairs is quite well correlated with ticket price. This is plausible; the more runs you have, the more chairs you'd need to ferry people to them! Interestingly, they may count for more than the total skiable terrain area. For sure, the total skiable terrain area is not as useful as the area with snow making. People seem to put more value in guaranteed snow cover rather than more variable terrain area.
 
 ![correclations_heat](https://user-images.githubusercontent.com/67468718/103321593-46df9000-49ef-11eb-95e4-ed68a07ca5b8.JPG)
 
  * **Feature Correlation Scatterplots**: Correlations, particularly viewing them together as a heatmap, can be a great first pass at identifying patterns. But correlation can mask relationships between two variables
     * There's a strong positive correlation with vertical_drop.
     * fastQuads seems very useful. Runs and total_chairs appear quite similar and also useful.
    
![resort_Scatter](https://user-images.githubusercontent.com/67468718/103321868-8d81ba00-49f0-11eb-9fb6-26dc1a4c91b1.JPG)

## Pre-Processing and Training Data: 
  * **Linear Model**: In the process of building the linear model, missing values were imputed with the median and mean values. If ticket prices were predicted using the linear model, they would be off by about $9. However, the initial linear model was overfitting and needed to be adjusted by the number of features. Through cross-validation, the value of k was set to eight features to focus on: vertical_drop, Snow Making_ac, total_chairs, fastQuads, Runs, LongestRun_mi, trams, and SkiableTerrain_ac. These features fit our initial assumptions from EDA.
  
  * **Random Forest Model**: Was developed. Like the linear model, missing values were imputed with the median and mean values. While imputing the median was helpful, it was not helpful to scale the features. The random forest model revealed that the top four features to consider are fastQuads, Runs, Snow Making_ac, and vertical_drop.
    
  * **Final Model Selection**: After testing both the linear model and random forest model, the project will be moving forward with the forest regression model. Comparison of the two demonstrated that performance on the test set was consistent cross-validation results. Additionally, the cross-validation mean absolute error was lower using the random forest regressor.
  
## Recommendations: 
  * Our Model suggests that Mountain Resort’s ticket price is lower than the predicted model by 16.31%, and the resort have many potential scenarios for either cutting costs by closing runs or increasing ticket price by increasing vertical drop, adding acres snow making or increasing the longest run.
  * Increasing the vertical drop by 150 ft would increase the ticket price by 10.44% from $81 to $89.46, resulting in revenue increase by $14,811,594.
  * Adding 2 acres of snow making would increase the ticket price by 12% from $81 to $90.75, resulting in revenue increase by $17,068,841.
  * When it comes to closing up to 10 used Runs, our Model predicted the following: 
    * Closing one run will have no impact on Ticket price or revenue.
    * Closing 2 runs reduce support for ticket price and so revenue by $0.4 and $750,000 respectively. 
    * Closing down 3 runs, it seems they may as well close down 4 or 5 as there’s same loss in ticket price and revenue by $0.67 and $1.250M respectively.
    * Closing 10 runs reduce support for ticket price and so revenue by $1.71 and $3M respectively.
    * Because we don’t know the operating cost per used run, we can’t determine how much cost saving will be offset the loss in revenue after closing more than one run.
       
<p align="center">
  <img width="550" height="500" src="https://user-images.githubusercontent.com/67468718/103326653-3d155700-4a06-11eb-8e4f-c90e7c3a866d.JPG">
</p>

    
## Conclusion: 
After applying our Model for ski resort ticket price and leverage it to explore Big Mountain Resort’s potential scenarios for increasing revenue, we can conclude that:
  * The best scenario where we managed to gain the highest revenue increase possible was by increasing the vertical drop by 150 ft, adding one Chair Lift, adding one run and adding 2 acres of snow making cover. This scenario has increased ticket price by 12% from $81 to $90.75, resulting in a bottom-line increase by $15,528,841 (After deducting operating costs = $1.54M).
  * Due to lack of data in regards of operating cost per used run and weekdays ticket price, our model cannot recommend closing down used runs or implementing a dynamic ticket pricing.
   
<p align="center">
  <img width="760" height="600" src="https://user-images.githubusercontent.com/67468718/103326714-849be300-4a06-11eb-9cad-8a898f6f9319.JPG">
</p>


    
    

    
    
    






