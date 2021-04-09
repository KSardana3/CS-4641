<small>Group: Krishna Sardana, Sanjot Singh, Saloni Shah, Sofia Fernandez Chacin, and Monica De Armas</small>

## Introduction

Pairs trading is an algorithmic trading strategy where trading occurs based on the idea that pairs of securities will always revert back to their historical spread. In order to make a profit, investors go long and short during the period when the spread between these two stocks diverges. When the spread returns to its historical mean, at least one of the positions will result in a profit. Trading on pairs of stocks in the same industry is the beneficial because they will react to similar market factors, therefore, having similar price variations. Once investors identify a pair of stocks, they verify the prices of the stocks are cointegrated before trading them. Investors can trade using various statistical thresholds that will allow them to figure out if the current spread is near the historical mean spread or not.

## Problem Statement

We aim to employ Machine Learning to find the ideal pair of stocks and predict their future spread which we can trade upon. Predictive models in the stock market are mainly used to learn about the upcoming fluctuation of different securities. Attaining an accurate projection leads to a potential increase in return for investors. Machine Learning is useful in this context because there’s a large range of methods that have the potential to discover patterns in datasets, leading to important resolutions.

## Methods

Our first method OPTICS is an unsupervised method similar to DBSCAN that will result in unique clusters of high density. This will allow us to take a large random pool of stocks and cluster them. Then, we will conduct the Augmented Dickey Fuller Test (ADF) to find the cointegration between each stock in a cluster which will allow us to determine ideal pairs. Finally, we will use the LASSO regularized regression method to predict the future spread between a pair which can be used to determine the z-score to trade on.

## Results

Ideal results will provide information regarding which correlated stocks are diverging in order to identify which stock should be opened on the long position and which should be opened on the short position. Our analysis is based on the assumption that the spread of a pair of correlated stocks will eventually converge. 

We started by pre-processing the data by taking the raw dataset which had vertically stacked close prices as shown:
d ate 
A 
AAPL 
ABBV 
YUM 
ZBH 
ZION 
ZTS 
2013- 
02-08 
45.08 
14.75 
78.9 
67.8542 
3625 
27.09 
7585 
24.14 
33.05 
2013- 
02-11 
446 
1446 
7839 
68 5614 
35 BS 
2746 
75 65 
2421 
33 26 
2013- 
02-12 
44 62 
1427 
78_6 
66 8428 
35 42 
27 95 
7 î44 
2449 
3374 
2013- 
02-13 
4475 
14 
78.97 
3527 
28.26 
6441 
24_74 
33.55 
2013- 
02-14 
4458 
13_gg 
78_84 
3657 
2847 
63_89 
76_34 
24_53 
3327 
2013- 
02-15 
42 25 
14_S 
65 7371 
37 58 
28 28 
63 99 
759 
24 34 
3398 
2013- 
02-19 
43.01 
14.26 
80.72 
657128 
38.19 
28.76 
76.11 
24.69 
33.34 
2013- 
02-20 
42.24 
13.33 
79.5 
641214 
3861 
27 _ 96 
7531 
24.14 
3272 
2013- 
02-21 
41.63 
13.37 
79.06 
63.7228 
38.78 
27.68 
6505 
73.87 
23.73 
3256 
2013- 
02-22 
13.57 
79_21 
644014 
3846 
27_79 
45 
74_14 
2404 
32_59 
2018- 
01-25 
7386 
5305 
120.92 
171.11 
1083 
7324 
124.74 
53.02 
7925 
2018- 
01-26 
74 82 
53 07 
1 23 64 
171 51 
123 21 
74 41 
862 
126 23 
54 02 
8009 
2018- 
01-29 
7453 
52.68 
12289 
167.96 
12231 
73.41 
127.39 
5419 
79.18 
2018- 
01-30 
72.99 
52.59 
119.27 
166.97 
11588 
7307 
84.59 
125.94 
5393 
73.35 
2018- 
01-31 
7343 
5432 
11699 
16743 
112.22 
72.26 
8459 
12712 
5403 
7673 
2018- 
02-01 
72.83 
53.88 
117.29 
167.78 
116_34 
74.84 
83.98 
128.19 
54.98 
77.82 
2018- 
02-02 
71.25 
52.1 
113.93 
1605 
11517 
8263 
12579 
5415 
75.78 
2018- 
02-05 
68 22 
49 76 
109 86 
1 56 49 
109 51 
72 66 
798 
123 18 
51 65 
73 83 
2018- 
02-06 
6845 
51.18 
112_2 
16303 
111_2 
7133 
8058 
1223 
52.52 
7327 
2018- 
02-07 
68.06 
sı_4 
10993 
15954 
113.62 
71.79 
8013 
120.78 
5402 
73.86 
505 rows x 1259 columns 


## Discussion

By utilizing  ML, investors no longer have to solely rely on regression for pair selection, and will achieve a higher return on their investment. Our model should be able to simulate mean-reverting stock pairs and differentiate them from those who have a non-stationary spread. Meaning, ML can identify stocks that do not belong to the same industry nor have similar characteristics but do have a correlation, increasing the possibility of making a profit.

It will be interesting to explore the impact of selecting distinct thresholds to signal a diverging spread between identified stocks. Selecting appropriate benchmarks for spread divergence may help reduce market-risk exposure, helping small-time investors achieve a consistent return regardless of the market.

## References

1. Sarmento, S., & Horta, N. (2020, May 04). Enhancing a pairs trading strategy with the application of machine learning. Retrieved March 03, 2021, from https://www.sciencedirect.com/science/article/pii/S0957417420303146 

2. Vidyamurthy, G. (2011). Pairs Trading: Quantitative Methods and Analysis. Hoboken: John Wiley & Sons. 

3. Chien-Feng Huang, Chi-Jen Hsu, Chi-Chung Chen, Bao Rong Chang, Chen-An Li, "An Intelligent Model for Pairs Trading Using Genetic Algorithms", Computational Intelligence and Neuroscience, vol. 2015, Article ID 939606, 10 pages, 2015. https://doi.org/10.1155/2015/939606.

4. Nugent, C. (2018, February 10). S&P 500 stock data. Kaggle. https://www.kaggle.com/camnugent/sandp500.

