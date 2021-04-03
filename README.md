
# Zillow Housing Data Analysis

## Data and Introduction
In this bog post we will deal with the time series analysis of of the Zillow data set which details the average house prices in every zipcode between April 1996 to April 2018.
There are overall 14723 Zipcodes which is a lot of data.  The question that we address in this project is the following. Imagine a real estate company has contracted us to analyze the data. The question that they want answered is

What are the 5 best zip codes to invest in?

Let us begin by visualizing the normalized ROI on first 200 zipcodes. We can clearly see the 2008 financial crisis in the data

![Alt text](/Figures/roi_200.png?raw=true "ROI")

We can also plot the average cost of all zipcodes

![Alt text](/Figures/average.png?raw=true "Average")

Because the prizes dont stabilize till 2012, we will mostly consider post 2012 pries for our analysis

## Analysis
What is the definition of best?
### Naive Analysis
One naive definition  of the best zipcodes to invest in can simply be the return on investment "ROI" they generate every month. Assuming the monthly ROI is x we can write 
x = (1/n)*Log(final_price/initial_price) where n is the number of months.

Doing the Naive ROI analysis only considering returns after 2012 we get the following zipcodes
![Alt text](/Figures/roi_2012_nona.png?raw=true "Average")

We do a SARIMA analysis on the last 6 years if post-recession data and use two different metrics for predicting best zipcodes to invest in (best average returns and best Sharpe ratio.) See notebook for more details

### SARIMA Analysis

The data we have for the individual cities is not stationary at all. In order to perform an ARIMA analysis we first need to make our data stationary. Also as noted above we will only analyze data from the last Jan 2013 to April 2014 i.e. safely in the post-recession region. We will also restrict ourselves to the zipcodes with SizeRanks < 1000 since processing the entire dataset is extremely time consuming. You can think of it as investment in the "big markets"

The best zipcodes based on the highest returns in our SARIMA analysis is shown below
![Alt text](/Figures/final_mean_d1.png?raw=true "Mean ARIMA")

The best investments ranked by their Sharpe ratio by
![Alt text](/Figures/final_sharpe.png?raw=true "Sharpe")


## Conclusion

Looking at the fraction of common entries (when we do the SARIMA analysis for 5 year data vs 6 year data),  we can see that the fraction of common zipcodes quickly goes to 50% within the first ~ 40 zipcodes

![Alt text](/Figures/common.png?raw=true "ROC")

This gives us confidence in the stability of our analysis

## Blog

https://aghalsasi-datascience.blogspot.com/2020/01/zillow-data-time-series-analysis.html

## Navigating the Repsoitory

The entire analysis is in Zillow_Data_Analysis.ipynb