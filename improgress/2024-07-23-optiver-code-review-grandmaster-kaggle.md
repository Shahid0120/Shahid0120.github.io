---
layout: single
classes: wide
title: "Kaggle Model Review: Optiver - Trading at the Close"
header:
categories:
  - ML Model Review
author_profile: True
---
Recently I've been learning about time series analysis, numerical analysis and financial analysis. So I've wanting to review the latest optimal models for this process. 
After looking online i came across Kaggle competition "Optiver - Trading at the Close" and luckily for me the solution to the top solution is avaliable. So i would like to have a run down of what i learnt by analyzing the model and code.

# Goals of the Regression Model

"Predicting the closing price movements for Nasdaq stocks"
through order book and the closing auction of the stock.

# Overview - Why we need a model?

(1) Peak intensity of stock exchange is during the last 10 minutes of stock closing times.
(2) Closing Times are characterized by 
    - High Volatility 
    - Rapid Price Fluctuations
During the last 10 minutes there is a "Nasdaq Closing Cross auction" which established closing prices for stocks.

## What do Traders do during the Closing Times

During the last 10 minutes traders "merge order book data with auction book data". Thus, the challenge is the predict closing price movement using (1) order book (2) closing auction book.

## What is a Auction, Order book and Auction order book?
for a detailed introduction read [Optiver - Trading At The Close Introduction](https://www.kaggle.com/code/tomforbes/optiver-trading-at-the-close-introduction)

### Auction
Auction : Process of allowing buyers and seller to interact "directly" within the financial regualtions. Types of auctions includes;
  - Opening Auction: sets the intial prices for trading day for securities
  - Closing Auction: sets final prices of security at the end of the trading day 
  - Reverse Auction : how governments sell securities, usually undler buyer agress prices

THere are many more, but for this they focused on closing auction. The closing auction it determined by "price at which the maximum number of shares can be matched".


### Order Book
Electronic List of buyers (bid) and sellers (ask) there is a continual trade between number of bids vs number of ask. Say there exist 9 ask at price of 9 then if someones big for 10 at price of 9, then the seller will receive for 9 shares, and thus the new order book contains 1 bid at price of 1 rather then the original 9 ask at price of 9. The range of price level is continuous for 0 to inf. 

### Auction order book 
Auction order books is different to the order book is called "uncross" price, rather then only referring to specific price level for interactions between bid and ask, It now allows interactions between price levels. In the order books the order are immediately match at price levels, but in Auction order books, orders are matched in auction closing time. 

Say the price levels are 10, 9, 8. Suppose, 
- ask : {10: 1,  9: 3, 8:2} 
- bid {10: 4,  9: 2, 8:1}
Then at auction end times. for bid price of price level 10, since there is only 1 ask price of 10 it will match it and then go down to cheap price level, aka 9 then do the remaining 3 bid orders. so after the first big price level 10. we have,
- ask: {10: 0,  9: 0, 8:2}
- bid {10: 0,  9: 2, 8:1}
Now it goes down to price level 9, so for ask at price level 9 there is none so it goes down a price level to 8 and since there is only 1, the bider has only 1 order. unfortunately bider 8 doesn't buy any order since there is none remaining. 
So the final auction order book is 
- ask : {10: 0,  9: 0, 8:0}
- bid {10: 0,  9: 0, 8:1}

## Combined book 
Combing two books allows more accurate reflection of market's buying and selling interest at different price levels, allowing price discovery. 

# How the models were evaluated
Each solution was evaluated Via Mean Absolute Error

$$
\begin{align*}
MAE = \frac{1}{n} \sum_{i=1}^n |y_i - x_i|
\end{align*}
$$

Which makes logical sense since we average the model prediction $$ y_i $$ with our observed $$ x_i $$.

## Solutions Overview
From looking at multiple solutions i found that the most used models were
- XGboost 
- CatBoost 
- Lightgbm
- Transformer
- LSTM
Most of the top solutions used  Moving Average windows, Online training, Ensemble learning
## interesting discussion  
Key observations
(1) Cross validation score doesn't always lead to reducing MAE.
(2) Local Cross Validation.
(3) Implementing a Advanced Purging CV. 


By far the most common were XGBoost, CatBoost and LightGBM. So lets talk about it!


# XGBoost 



