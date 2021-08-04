# Capstone Project: Planet Jordan
## Room demand forecast and hotel chain business analysis
## Table of Contents:

### Part 1
1. Background 
1. Problem Statement 
1. Executive Summary
1. Data Cleaning  

### Part 2
1. Exploratory Data Analysis 

### Part 3
1. Modeling    
    1. ARIMA
1. Model evaluation and summary
1. References 

## Background
**Client brief**
- Our client is Planet Jordan, an international hotel group owned by billionaire sportsman and entrepreneur Michael Jordan
- They have five hotel chains with widespread distribution across Greater China
- Michael Jordan is very focused on the staycation market (i.e. domestic residents staying in a local hotel for a vacation, to feel like they are getting away from home)
- Planet Jordan have historically been very strong in this sector and run a loyalty program, “The Staycation Card” to encourage repeat business
- Recently Michael Jordan has noticed declines in demand and suspects it is because competitors are developing their own programs to take on Planet Jordan in key cities or across key chains
- He has asked his sales & marketing executives to prepare him with some insight on what is happening and some recommendations on what to do – they are due to present to him in three months and have engaged us in support
- Their sales & marketing team are visiting Shanghai and have asked for a preliminary meeting with us – they are primarily interested in how we will approach the project, but they are also looking for some preliminary insight on which cities and hotels are the most important to target in the project 

## Problem Statement
**Instructions**
- Produce a deck to present to the Planet Jordan Sales & Marketing team 
- Your presentation should focus on how you are going to address this question and what analyses your team will perform.  You should also provide an initial point of view on which cities and hotels should be the focus of the project
- You have been provided with some supporting excel data entitled ‘Planet Jordan Hotels_Raw Data’ – this extract will be helpful for your point of view and you may use it however we wish. You may also choose to reference other external data, but note that we are most interested in how you structure your thinking about the problem rather than your ability to regurgitate existing research 
- Add a predictive analytics by forecasting demand for rooms.
- There will be no opportunity to ask questions before your final presentation, so please call out any assumptions you have made at that time

## Executive Summary
### Data cleaning
After loading in the data, we took a quick look at the data to get a general feel of the data that we have to be dealing with. First we changed the column names to lower case for easier handling and then checked for null values, followed by checking for unusual values in both categorical and numerical columns. We found some errors and corrected them. Next we handled the null values by dropping most of them since it didn't affect the data much. Finally we renamed some columns for easier referencing later on.

### EDA
We further streamlined the dataset by dropping a few more columns after cross referencing them with each other. We plotted some columns against the 2 revenue columns and found some discrepancies, made some assumptions, corrected them and created a few columns for analysis purpose. This is a preliminary analysis. A more detailed analysis will be done on Power BI. Data is prepped and ready for modeling and Power BI analysis.

### Modeling
For this analysis, we chose an ARIMA model to conduct a time series forecast to predict rooms sold/demand over a daily interval using the series past values. It is important to note that there is a steep climb at the first part and a sharp dip in the last part of this dataset. After many rounds of experimenting with different train/test split ratio, due to the nature of this particular dataset, we have come to the conclusion that the sharp increment/decrement in the data made it relatively unfriendly to conventional data science machine learning modeling. The machine tend to overfit on the training data and the predictions are heavily skewed. With that, we declare that a deployable model is not achievable. On that note, we do offer a model without the sharp increment/decrement in the data and to make a forecast with a 95% confidence interval. 

### Business analysis
**Overview**


From the Power BI deck, we see that this analysis is conducted on a dataset over a period of approximately 14 months from July 2012 to August 2013. There are a total of 82 hotels operating in 23 cities across the nation China. The chain generated a total of 10.09m USD during this period, out of which 7.74m USD is from room revenue and the remainder from other sources like room service and spa etc. One thing we note is that the check in counts and revenue in each city stayed pretty consistent throughout this period with not much changes or sudden jumps which means the business is operationally stable.


**Metrics and rules**


For this analysis, we will be using check in counts and revenue as the metrics. We will also be employing the Pareto Principle, also known as the 80/20 rule, which asserts that, in our case, 80% of our revenue come from 20% of our product(hotel).


**Analysis by City**


Going by the Pareto Principal, we will focus in on the top 6 hotels (20% of 23 cities rounded up + 1 to cover a slightly wider range). We calculated the average total revenue per city to be around 439,000 USD and average check in count per city to be 4479. Top 6 Cities by total revenue are Shanghai, Hangzhou, Suzhou, Nanjing, Guangzhou and Jiuzhaigou and top 6 cities by check in count are basically the same top 5 but with Wuxi coming in at the 6th position. One reason why these cities are making it into the tables is because they have more hotels so generally it makes sense that more hotels means more check ins and higher revenue and that brings our attention to 5 cities: Jiuzhaigou and Wuxi for good reasons and Chengdu, Shenzhen and Chongqing for bad ones. 


With 2 hotels in the city, while Jiuzhaigou is 57% below the nation's average in check in counts, they did very well in bringing in revenue to rank at 6th. On the other hand, Wuxi, with only 1 hotel, while missing the total revenue average by around 29%, managed to boost a high check in count to rank, again, at 6th place. It is worth zooming into these 2 cities to find out more about how and what they have been doing to bring in good results like they have. 


According to the Chinese city tier system by Yicai global 2017, Shenzhen is a tier 1 city and Chengdu and Chongqing are new tier 1 (used to be tier 2 in the older system) cities. With 5 hotels and being a tier 1 city, it is worrying to see Shenzhen performing below nation's average in both metrics, specifically near 30% below for both. Similarly, being a new tier 1 city, with 6 hotels in Chengdu and 4 in Chongqing, these 2 cities disappointedly did 45 to 67% below average in both departments.


**Cities to focus**

| City          	| Reason                           	|
|----------------	|----------------------------------	|
| **Jiuzhaigou** 	| High revenue low check in counts 	|
| **Wuxi**       	| High check in counts low revenue 	|

| City          	| Reason                           	|
|---------------	|----------------------------------	|
| **Shenzhen**  	| Low in revenue & check in counts 	|
| **Chengdu**   	| Low in revenue & check in counts 	|
| **Chongqing** 	| Low in revenue & check in counts 	|

**Analysis by hotel**


Using the same 20% rule, we will focus in on the top 17 performing hotels. A simple comparison showed us that the top 17 hotels by total revenue are the same as the ones by check in counts which made perfect sense because these 2 metrics are closely correlated where most of the revenue are generated from selling rooms. All hotels except Suzhou City Rodman, Hangzhou Grand Jordan and Shanghai Grant V performed above national average on both metrics. Those 3 fared slightly below in the revenue section by between 7 to 40%. 


Having acknowledged the correlation between check in counts and revenue, there are two categories we are particularly interested in: low check in counts high revenue and high check in counts low revenue. In the first category, we have Shanghai Urban Pippen, Hanzhou Pippen, Shanghai East Rodman and Shanghai City Pippen. These 5 hotels brought in relatively high revenue with a comparatively low check in counts. 2 points of interest may be how they managed that and also how to increase the check in counts.


In the second category we have Guangzhou Urban Jordan, Shanghai Grant I and Wuxi Pippen. Likewise from the previous category, it would be interesting to find out why these 3 hotels are generating relatively low revenue when so many rooms were sold and also on the positive end, dive deeper into how they managed to sell so many rooms.


**Hotels to focus**

| Revenue below average     	|
|---------------------------	|
| **Suzhou City Rodman**    	|
| **Hangzhou Grand Jordan** 	|
| **Shanghai Grant V**      	|

| Low check in counts high revenue 	|
|----------------------------------	|
| **Shanghai Urban Pippen**        	|
| **Hangzhou Pippen**              	|
| **Shanghai East Rodman**         	|
| **Shanghai City Pippen**         	|

| High check in counts low revenue 	|
|----------------------------------	|
| **Guangzhou Urban Jordan**       	|
| **Shanghai Grant I**             	|
| **Wuxi Pippen**                  	|

**Analysis by member**


We generated a Decomposition Tree on the page Revenue decomposition to provide some analysis by members. Using this tree, we can drill down from city to individual hotel to every member who have stayed there and which city they are from. This can be useful for the Sales & marketing team for target precision marketing purpose. It is also shown that our chain is generating 75% of revenue from Platinum members and the remaining 25% from gold members,  as well as 68% from tier 1, 31% from tier 2 and less than 1% of revenue from tier 3 members. This is good evidence that our loyalty program 'The Staycation Card' is working well and we should work and further capitalize on it.


**The decline**

Addressing the sudden and sharp dip in check in counts starting from July 2013, we went ahead to conduct some research and found two possibilities.
- 2013 Southwest flood
- Xi Jinping's ascension to power

In July 2013, much of southwest China experienced heavy rainfall that led to widespread flooding. Sichuan was the hardest hit. An estimated 6 million lives were disrupted by the floods. Following that, typhoons and storms made landfall over China devastating northern, northeastern and southern provinces affecting, in total, an estimated 72 million lives. As we can see on our deck, that is EXACTLY how our hotels are distributed across the country. This natural disaster probably single handedly destroyed the sales during this period forcing most, if not all of bookings to be canceled. 


The second reason could be due to Xi Jinping's ascension to power in March 2013. Upon taking office, Xi launched a far reaching campaign against corruption where he outlined the 'eight-point guide' listing rules intended to curb corruption and waste during official party business including traveling only when necessary and reducing entourage to bare minimum. The campaign immediately went into strict enforcement causing many booked trips to be canceled or reduced in size. While we understand that our group is focused more on staycation than business traveling market, this was a major event during that time which hugely affected hotel industry. Even if it did not have a direct impact on us, there could still be some degree of indirect effect.

**Recommendations**


While it is impossible to control natural disasters, we can
1. Change marketing tactics
- Storms and typhoons are mostly seasonal and weather stations usually issue warnings before they happen. While dealing with a natural disaster, we can avoid waste in marketing by pausing marketing campaigns, replacing regular email campaigns with messages crafted for an emergency and anticipate cancellations.
2. Regulate updates
- We can maximize our social media platforms to offer updates to guests, concerned parties and community and keep guests and interested parties notified on the progress of the events.
3. Recovery
- Ensuring safety of guests and employees should be primary concern. If possible, keep track of any damages during the event to better formulate cleanup plans and focus on recovery after the event for reopening.
4. Diversification
- To prevent being affected too much by a certain group (in this case, business travelers), we can diversify and target different market groups like family or couple so we are not dependent on any specific groups.
