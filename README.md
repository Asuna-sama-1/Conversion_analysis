# Conversion_analysis

Sales Conversion Analysis  


In the insurance industry, customer conversions don’t happen in a short time like website click-throughs, yet it’s usually delayed in real life. It’s important for businesses to track conversion rates as time passes. 
Sale Funnel

Before we dive into any business analysis, we should understand the sale funnel. The funnel chart below shows multiple conversion rates along the user journey. We can find the bottleneck, aka, where the customers are lost. 

### 1.1 Bottleneck Research

The data tells us that during the time period when the data was collected, 75% of users requested price and our agent has reached out to 75% of them, but only 7.7% of them are successfully converted.
This means most of the customer losses happened AFTER customer submitted their information. There are some directions that we can look into
1.  How long is the wait time in the queue?
  There is a high chance of losing customers if we let them wait for too long. Reduce the wait time if this is the root cause.
 2.  Agent's strategy when speaking to a customer.
How do we contact our customers? by phone? or by email?
When are we contacting our customers? morning? night? weekdays? weekends?
3. There are also other areas we would look into:
UI/ UX issue; when customers installed the app, is it easy for them to navigate the app and know how to submit their information?
### 1.2 Average Wait-time VS. Conversion rate at each stage

Here we look at our conversion rate for each stage. From the graph below we can see that the average wait time and the conversion rate for each process stage are not correlated. 


### 1.3 Total conversion rate in 90-day intervals 


90 days Interval 
Conversion 
Rate
% of total
 conversion rate
  1st  
4.13%
95.26%
   2nd  
0.15%
3.34%
  3rd  
0.04%
0.85%
     4th  
0.02%
0.51%




From above, we can see that majority of the conversions happened within the first 90d after installation, which means we should try to invest most on engaging with our customer during this time frame. In this case, we define conversion rate by taking the number of sold customers and dividing by the number of total installations during a 90 days time period. 
Now, Let’s take a closer look at the days.

## Conversion Rate Forecasting 
### 2.1 Conversion Rate by Quarter 

According to the dataset, the initial starting date for this analysis is the first installation date, which is ‘2018-10-10’. 90 days after this day accounts for one quarter. The reason we are starting with the first installation date instead of a common starting date for each quarter is due to the size of our dataset. If we are working with many years of historical data, then I would suggest working with ‘01–01’ for a better understanding of the seasonality.

 Each element on the x_axis indicates a 90 days interval. We can see that the conversion rates are increasing in a small amount each quarter. Here we should note the last row of data into consideration since we do not have enough date data to support this time period. 



### 2.2  Forecasting 

Before conducting time series forecasting, we check the stationarity first. By plotting the rolling mean and rolling standard deviation. the rolling mean and rolling standard deviation are almost flat with time. Therefore, we can conclude that the time series is stationary.



ARIMA 

Differencing subtracts the current value from the previous and can be used to transform a time series into one that’s stationary.


Left: line plot of residual errors, suggesting that there may still be some trend information not captured by the Model. 
Right: density plot of residual error, suggesting the errors are Gaussian. 

The test RMSE IS 0.014 and the above graph is the forecasts vs. actual outcomes. The model could use the further turning of the p,d, and maybe even the q parameters. 


Prophet by Meta

The model here is trained without yearly seasonality. The total number of rows in the original dataset was 723 and we see that the future data frame that we created for prediction contains historical dates as well as additional 360 dates. NOTE: more iteratively graph is available in the .ipynb file.



## Optimizing customer acquisition spend
### 3.1 Conversion Rate vs. Time 

The following graphs showed the monthly, weekly, and hourly conversion rate for our dataset. The bar plot indicates the number of users who are converted, and the line indicates the conversion rate for the period of time. 
Monthly:  2019-05 has the highest conversion rate without having the highest number of sold users. 
Weely: Users are mostly to make purchases on Tuesday, Friday, and Saturday. 
Hourly:  there are fewer people installing our app before 9 am; however, at 10 am, the conversion rate increased a large amount, which means we should definitely use this time to acquire customers. The conversion numbers are also high after 5 pm when people are off work.





### 3.2 Cost of Acquisition 
Cost of Acquisition =( number of installs * cost per install) / conversion rate
Take cost per install = $0.01

Goal is to keep the cost of acquisition as low as possible. 
Weekly: Although the graph in 3.1 showed a lower installation number on the weekends, the cost of acquisition is relatively low than on weekdays. 
Dailly: The lowest cost of acquisition is at 10 am, and it also has a relatively high conversion rate. Moreover, from 4 pm to 11 pm are also a pretty good time frame to take action for the marketing team. 


Overall, if we are going to spend on a particular day/time for paid marketing to acquire customers, we should do it during the weekend morning around 10 for the lowest cost and higher return. 


Check out the blog post here: https://medium.com/@asunadch/sales-conversion-analysis-efb2335f3f12
