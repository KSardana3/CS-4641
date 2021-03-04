## Introduction

Pairs trading is an algorithmic trading strategy where trading occurs based on the idea that pairs of securities will always revert back to their historical spread. In order to make a profit, investors go long and short during the period when the spread between these two stocks diverges. When the spread returns to its historical mean, at least one of the positions will result in a profit. Trading on pairs of stocks in the same industry is the beneficial because they will react to similar market factors, therefore, having similar price variations. Once investors identify a pair of stocks, they verify the prices of the stocks are cointegrated before trading them. Investors can trade using various statistical thresholds that will allow them to figure out if the current spread is near the historical mean spread or not.

## Problem Statement

We aim to employ Machine Learning to find the ideal pair of stocks and predict their future spread which we can trade upon. Predictive models in the stock market are mainly used to learn about the upcoming fluctuation of different securities. Attaining an accurate projection leads to a potential increase in return for investors. Machine Learning is useful in this context because there’s a large range of methods that have the potential to discover patterns in datasets, leading to important resolutions.

## Methods

Our first method OPTICS is an unsupervised method similar to DBSCAN that will result in unique clusters of high density. This will allow us to take a large random pool of stocks and cluster them. Then, we will conduct the Augmented Dickey Fuller Test (ADF) to find the cointegration between each stock in a cluster which will allow us to determine ideal pairs. Finally, we will use the LASSO regularized regression method to predict the future spread between a pair which can be used to determine the z-score to trade on.

## Potential Results

Ideal results will provide information regarding which correlated stocks are diverging in order to identify which stock should be opened on the long position and which should be opened on the short position. Our analysis is based on the assumption that the spread of a pair of correlated stocks will eventually converge. The performance metrics of our general model will serve to identify the associated risk of the trading strategy.

## Discussion

By utilizing  ML, investors no longer have to solely rely on regression for pair selection, and will achieve a higher return on their investment. Our model should be able to simulate mean-reverting stock pairs and differentiate them from those who have a non-stationary spread. Meaning, ML can identify stocks that do not belong to the same industry nor have similar characteristics but do have a correlation, increasing the possibility of making a profit.

It will be interesting to explore the impact of selecting distinct thresholds to signal a diverging spread between identified stocks. Selecting appropriate benchmarks for spread divergence may help reduce market-risk exposure, helping small-time investors achieve a consistent return regardless of the market.

## References

1. Sarmento, S., & Horta, N. (2020, May 04). Enhancing a pairs trading strategy with the application of machine learning. Retrieved March 03, 2021, from https://www.sciencedirect.com/science/article/pii/S0957417420303146 

2. Vidyamurthy, G. (2011). Pairs Trading: Quantitative Methods and Analysis. Hoboken: John Wiley & Sons. 

3. Chien-Feng Huang, Chi-Jen Hsu, Chi-Chung Chen, Bao Rong Chang, Chen-An Li, "An Intelligent Model for Pairs Trading Using Genetic Algorithms", Computational Intelligence and Neuroscience, vol. 2015, Article ID 939606, 10 pages, 2015. https://doi.org/10.1155/2015/939606.

4. Nugent, C. (2018, February 10). S&P 500 stock data. Kaggle. https://www.kaggle.com/camnugent/sandp500.

