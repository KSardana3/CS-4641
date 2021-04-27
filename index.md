<small>Group: Krishna Sardana, Sanjot Singh, Saloni Shah, Sofia Fernandez Chacin, and Monica De Armas</small>

## Introduction

Pairs trading is an algorithmic trading strategy where trading occurs based on the idea that pairs of securities will always revert back to their historical spread. In order to make a profit, investors go long and short during the period when the spread between these two stocks diverges. When the spread returns to its historical mean, at least one of the positions will result in a profit. Trading on pairs of stocks in the same industry is the beneficial because they will react to similar market factors, therefore, having similar price variations. Once investors identify a pair of stocks, they verify the prices of the stocks are cointegrated before trading them. Investors can trade using various statistical thresholds that will allow them to figure out if the current spread is near the historical mean spread or not.

## Problem Statement

We aim to employ Machine Learning to find the ideal pair of stocks and predict their future spread which we can trade upon. Predictive models in the stock market are mainly used to learn about the upcoming fluctuation of different securities. Attaining an accurate projection leads to a potential increase in return for investors. Machine Learning is useful in this context because there’s a large range of methods that have the potential to discover patterns in datasets, leading to important resolutions.

## Data Collection

The dataset that we chose was the stock price data from the S&P 500 from 2013 to 2018. This includes the open and close prices of the day, the high and low prices of the day, and the volume traded. However, the column that we were interested in was the close prices as we decided they would be the best data to trade upon for the algorithm. We started by pre-processing the data by taking the raw dataset which had vertically stacked datapoints as shown:

<img src="https://raw.githubusercontent.com/KSardana3/CS-4641/gh-pages/GetImage2.png" width="400" height="400"/>

This was not the way we wanted the data to be formatted as we wanted to have each row show the close prices of different stocks over the five years. Therefore, we processed the data and were able to put each individual stock in time series order as shown:

![Processed](https://raw.githubusercontent.com/KSardana3/CS-4641/gh-pages/GetImage.png)

Then, we found the daily percent change which is important as we are looking for pairs of stocks that have similar percent changes day over day which is what we pass into the PCA model.

## Methods

Chronologically, our first ML method, PCA will lower the dimensionality of the dataset by lowering the 1259 days of closing prices down to 300 principal components. Then, we will use OPTICS, which is an unsupervised method similar to DBSCAN that will result in unique clusters of high density. We picked OPTICS over DBSCAN because it can handle clusters of varying density which is one of DBSCAN's weaknesses. This method will allow us to take a large pool of stocks and cluster them based on their daily percent change.  Then, we will conduct the Augmented Dickey Fuller Test (ADF) to find the cointegration between each stock in a cluster which will allow us to determine ideal pairs within each cluster. Finally, we conducted both LASSO and Ridge regularized regression methods to predict the future spread between an ideal pair which can be used to determine the z-score to trade based upon. Utilizing the z-scores that we predicted, we backtested the pairs trading algorithm and tracked generated returns.

## Process

Ideal results for the clustering will provide information regarding which correlated stocks are diverging in order to identify which stock should be opened on the long position and which should be opened on the short position. Our analysis is based on the assumption that the spread of a pair of correlated stocks will eventually converge. Therefore, by clustering based on percent changes and then looking for cointegration will guaruntee convergence to the mean spread.

We applied PCA the dataset and lowered the 1259 days of closing prices for each stock down to 300 components. The results were as follows (example of first 9 components):

![PCA](https://raw.githubusercontent.com/KSardana3/CS-4641/gh-pages/GetImage3.png)

The next step was to cluster the stocks based on these 300 components for each stock. We applied OPTICS clustering on the PCA result and the clustering was as follows:

![Clustering](https://raw.githubusercontent.com/KSardana3/CS-4641/gh-pages/Clustering.png)

This is an example of 3 stocks in plotted from cluster 0:

<img src="https://raw.githubusercontent.com/KSardana3/CS-4641/gh-pages/ExampleStocks.png" width="400" height="250"/>

Our next step will be to find cointegrated stocks within these clusterings using the Augmented Dickey-Fuller Test:

<img src="https://raw.githubusercontent.com/KSardana3/CS-4641/gh-pages/CointegrationCode.png" width="600" height="500"/>

For each cluster, we run Dicky-Fuller Test on different pairs of stocks and look for the lowest p-value returned from the test. The two lowest p-value pairs were AIZ (Assurant) & ECL (Ecolab) and MPC (Marathon) & PRU (Prudential).

In order to implement the ridge regression model, we chose two stocks that are known to be highly correlated: Ford and GM. Using those, we trained our Ridge regression using 4/5 of the prices of these stocks. Using these weights, we fit our model onto the testing data and plotted our results. These are shown on the figure below:

![Index](https://raw.githubusercontent.com/KSardana3/CS-4641/gh-pages/GetImage5.png)

![Index2](https://raw.githubusercontent.com/KSardana3/CS-4641/gh-pages/GetImage6.png)

Our results are not ideal because the model only has one weight, so the regression shows a straight line as opposed to a polynomial fit. This does not accurately represent the spread between the stocks. In order to fix this, we will train the model with more features in order to generate a polynomial fit. Additionally, to find the spread between the data, we will define a spread function which will give us information about which stocks are converging and diverging.

Our lasso regression implementation was similar to our ridge. We used the same GM and Ford stocks and trained our model using 4/5 of the prices of the stocks. We obtained a fit from the data, but ran into the same issues as we did with Ridge regression. We will make the same modifications that we will make for the Ridge regression.

## Discussion

By utilizing  ML, investors no longer have to solely rely on regression for pair selection, and will achieve a higher return on their investment. Our model should be able to simulate mean-reverting stock pairs and differentiate them from those who have a non-stationary spread. Meaning, ML can identify stocks that do not belong to the same industry nor have similar characteristics but do have a correlation, increasing the possibility of making a profit.

It will be interesting to explore the impact of selecting distinct thresholds to signal a diverging spread between identified stocks. Selecting appropriate benchmarks for spread divergence may help reduce market-risk exposure, helping small-time investors achieve a consistent return regardless of the market.

## References

1. Sarmento, S., & Horta, N. (2020, May 04). Enhancing a pairs trading strategy with the application of machine learning. Retrieved March 03, 2021, from https://www.sciencedirect.com/science/article/pii/S0957417420303146 

2. Vidyamurthy, G. (2011). Pairs Trading: Quantitative Methods and Analysis. Hoboken: John Wiley & Sons. 

3. Chien-Feng Huang, Chi-Jen Hsu, Chi-Chung Chen, Bao Rong Chang, Chen-An Li, "An Intelligent Model for Pairs Trading Using Genetic Algorithms", Computational Intelligence and Neuroscience, vol. 2015, Article ID 939606, 10 pages, 2015. https://doi.org/10.1155/2015/939606.

4. Nugent, C. (2018, February 10). S&P 500 stock data. Kaggle. https://www.kaggle.com/camnugent/sandp500.

