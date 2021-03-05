# ITP449_Project_S-P500_Analysis

The dataset I used is SPY.csv which can be found within my repository. This dataset was downloaded from the Yahoo Finance Website.

Before In[1]:

This project seeks to analyze the S&P500 ($SPY) in several different mannerisms. First off, we tend to see Q4 earnings be the highest of all quarters for a considerable amount of companies due to excessive spending during the holiday season. If one were to purchase the S&P500 every year before the holiday season on November 1st, and proceeded to sell during Q4 earnings reports in mid February, could one expect to consistently generate a profit? How much profit/loss could one expect on average to generate through executing this strategy? As well, how could one expect to compare that strategy as opposed to just buying and holding the S&P500?

This project will also use several analytical and forecasting tools to analyze the correlation between market volatility and volume, as well to see if any commonly used forecasting models could accurately predict the price of the S&P500.

After In[2]:

Here I created two separate data frames, one called “finBeggining” which isolates the csv file containing the S&P500 data into a data frame containing just the information from the first day of November of each year. The data frame “finEnd” contains information from the date closest to the middle of February from each year. 

After In[31]:
 After running some mathematical analysis, I discovered that there 5 of the total 28 instances in which the market had been lower in February (post-Holidays) than in November (pre-Holidays). As shown in the output, had you purchased a share of the S&P 500 during the Pre-Holiday season and sold it in the Post-Holiday season every year, you would have made almost $208, compared to $345 had you just bought and held. This in itself displays that although you still would have generated a profit by buying pre-Holiday and selling post-Holiday each year, it would have been more beneficial to have just bought and held. 

After In[26]:

Here is a visualization of the price comparisons of the pre-Holiday prices vs the post-Holiday prices for each year.

After In[7]:

Here is a grouped bar chart displaying the price comparisons for each year as well, but this one allows one to spot a particular trend easier. This trend is that we tend to see pre-holiday prices be higher at the peak of the market prior to a crash (as one would expect), as well as at the lowest points of each particular crash. These peaks being 2000, 2008, and 2016. The low points being 2003 and 2009.

After In[23]:

Here is a graph displaying the point gain or loss in the S&P500 from each pre-holiday and post-holiday period. We see the mean difference is +7.42.

After In[9]:

Here is a graph displaying the percent increase or decrease in the S&P500 from each pre-holiday and post-holiday period. We see the mean percent charge was +5.09%

After In[28]:

Now that we’ve looked at price comparisons, we will now go into some other analysis through using different analytical tools and predictive models. Here we see the autocorrelation of the S&P500 closing price and volume. In the stock market, lower volume indicates the stock is more illiquid, which results in greater volatility. This is represented in these two graphs above. Autocorrelation hovers just slightly below 0 from lag=2000 to lag=4000 in the closing price graph. In that same interval, we see a negative autocorrelation of volume. The lack of correlation in the first graph indicates that there was high volatility in the market, which matches the lower volume being traded at that same interval.

After In[29]:

Here we applied the Facebook Prophet model onto the closing prices of the S&P500 from November 1st, 1993 until late February 2021. We see the prophet model does a fairly good job in of making in-sample predictions during times of relative market stability and lack of volatility. However, once strong volatility does hit, it is very difficult for the model to forecast these changes. We see this precisely towards more recent years beginning in 2019, when large instances of volatility cause large residuals to occur in regards to our prophet model.

After In[35]:

Here we use the predicted values (yhat) from the prophet model for Pre-Holiday and post-Holiday S&P500 prices and compare it to the actual (y) values. We see that the in-sample predictions for just the pre-holiday prices were fairly accurate, with an MAE of 3.724% for both pre and post-holiday prices. 

After In[30]:

Here we do an out-sample prediction with the prophet model. We once again see how the prophet model seeks the trend, avoiding volatility. This is evident by the drop off from when the in-sample data ends and the out-sample prediction begins. The model is analyzing the trend, rather than volatility, which could be beneficial for long term traders and less valuable for short-term traders. 

After In[24]:
Here we ran the ARIMA model with a (5,1,0) model on the closing price for all the closing prices from the beginning of November in 1993 until late February 2021. As we’d expect, we see the residuals being larger in times of market volatility. However, our lag choice of 5 actually helps our model adjust to this volatility slightly, as opposed to simply following the overall trend. We see the standard deviation is 1.868, meaning that 99.7% of the real closing values fall within +/- 5.604 of our ARIMA model’s prediction, meaning this ARIMA model fits the overall dataset relatively well. We see that times of volatility have the largest residuals, as one would expect. 

Conclusion:

Upon all our analysis and calculations, it is fair to conclude that in times of a bull market, even a very slight bull, one could expect post-holiday S&P 500 prices to be higher than pre-holiday prices. However, during times of a market peak or market low, one could expect the opposite to occur. This is not to say this is a for sure economical gain and one should not follow this logic precisely, but it is fair to conclude based off of the data. Overall, it would still be more economical for one to purchase a share of SPY and just hold it rather than continuously buying and selling as shown before. 

In terms of best fitting models, it is clear that Facebook’s Prophet model can predict overall trends of the closing price, however it struggles to deal with volatility. The ARIMA model also struggles a bit with volatility, however the relatively low standard deviation of residuals indicate that it also does an overall accurate job of predicting the S&P 500 prices. All in all, the market volatility from the past 2.5 years alters these models’ accuracy quite substantially, however if the market ever returns to relatively stable conditions, we could expect the prophet and ARIMA models to be able to give roughly accurate forecast of the S&P 500 price.
