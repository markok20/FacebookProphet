# Facebook Prophet

Nokia's future stock price development: How to make a complete prediction model with Facebook Prophet?

How will the stock price develop in the coming weeks or months? Can seasonal fluctuations be seen in the share price development? When is the closing price at the maximum level based on historical data? What is the closing price in 100 days?

I sought answers to these questions when I predicted Nokia’s share price performance based on historical data. The method is Facebook Prophet, which is suitable for predicting different types of time series data with seasonal variation. The prediction method has been specifically developed by the Facebook Data Science team.

The data was Nokia's closing price (USD) from 1 January 2015 to 31 March 2021. This historical data can be accessed, inter alia, at:

https://finance.yahoo.com/quote/NOK/history?p=NOK

I processed the material in Python, where I brought the appropriate libraries, including Pandas and Matplotlib, as well as Prophet. At the end of the article is a link to the Python code.

DISCLAIMER: The important thing is that this post is intended to be educational in nature, not intended to provide investment advice or to encourage the purchase of shares.

One of the benefits of Facebook Prophet is that it visualizes daily, weekly, and yearly variations and eliminates holiday effects when needed. In short, the mathematical formula of the Prophet is as follows:

y (t) = g (t) + s (t) + h (t) + e (t)
g (t) = trend
s (t) = seasonal variations (week, month, year)
h (t) = holiday effects
e (t) = error / error / noise

The Prophet model can be quickly adapted to data regardless of the number of observations and does not require a large amount of data preprocessing. The model also takes into account missing observations and confidence limits. In this paper, I show how I use the model to predict Nokia’s stock price.

First, the basic statistical characteristics for the period 1.1.2015-31.3.2021 are described, ie mean, median, minimum, maximum and standard deviation. It appears that over the past six years, the average closing price of the stock has been approximately $ 5.47, a maximum of $ 8.3 and a minimum of $ 2.42.

Next, visualize the closing price development. With regard to last year’s developments, I note that exchange rate developments turned sharply downwards due to the outbreak of the corona pandemic in March 2020 and turned sharply upwards with social media discussions in January 2021.

Next, a prediction model is constructed. In the model, we only use the date and the closing price, i.e. ds = date and y = the closing price for each day. I do not divide the data into teaching and test data, but adapt the model to the whole data and tell them to predict future developments based on this.

The model uses actual development for fitting (black dots) and predicts development with confidence limits. According to the 100-day forecast, Nokia's closing price will be around $ 4.3 at the beginning of July.

Next, the trend, i.e., weekly, seasonal, annual, and daily variation, is described. The trend shows that the stock price usually rises to its maximum level in early August and on Wednesdays. In addition, the development of the exchange rate in the future with its reliability limits will be seen.
