# M5 Forecasting - Accuracy

This is our working space for ["M5 Forecasting - Accuracy" on Kaggle competition.](https://www.kaggle.com/c/m5-forecasting-accuracy/)


# What is M5 Competition?
M5 or 5th Makridakis Competitions is a big forcasting challenge asking you to estimate, **as precisely as possible**, the point forecasts of the unit sales of various products sold in the USA by Walmart. 
 
### Data
* The sales information reaches back from Jan 2011 to June 2016. They are also given corresponding data on prices, promotions, and holidays.
* 42,840 hierarchical time series with for different levels: item level, department level, product category level, and state level.
* There are up to 3049 individual products from 3 categories and 7 departments, sold in 10 stores in 3 states: California (CA), Texas (TX), and Wisconsin (WI).

### Goal
You have been challenged to predict sales data of the next 28 days.

### Metrics
The metric used in the competition is Root Mean Squared Scaled Error (RMSSE): similar to Mean Absolute Scaled Error (MASE) which was designed to be scale invariant and symmetric. Note: it also captures hierarchical characteristic of the data.


# Our Models
| Idx 	| Description                                                                                                       	| Best Score  in public leaderboard 	|
|:---:	|-------------------------------------------------------------------------------------------------------------------	|-----------------------------------	|
|  1  	| LightGBM: Recursive approach; predicting the tomorrow sale using the prediction of today sale and so on. See [Baseline LightGBM](https://github.com/chameleonTK/m5-forecasting-accuracy/blob/master/Baseline%20LightGBM.ipynb) 	| 0.49409                           	|
|  2  	| LightGBM: Day-by-Day models; 28 models for each day which were trained separately. See [Day2Day LightGBM](https://github.com/chameleonTK/m5-forecasting-accuracy/blob/master/Day2Day%20LightGBM.ipynb)                        	| 0.59198                           	|
| 3   	| Financial approaches;  See [notebook](https://github.com/chameleonTK/m5-forecasting-accuracy/blob/master/financial_model.ipynb)                                                                                   	| ...                             	|
| 4  	| Attention models                                                                                   	| ...                             	|

### Note
**Feature Engineer Section**: We used `lag_7` `lag_28` `rmean_7_7`  `rmean_7_28`

1. `lag_7` captures the week-on-week similarity to represent behaviour that people are likely to shop this monday similar to the last monday.
2. `lag_28` captures the weekly similarity from a month-to-month perspective representing behaviour that people tend to shop more in the first week of the month (due to the fact that they get paid from their job)
3. `rmean_` or rolling mean is a good representation of the big picture of the whole week/month. This can capture useful information about monthly and seasonal behaviours.

[more intuition behide these features](https://www.kaggle.com/kneroma/m5-first-public-notebook-under-0-50/comments)



### External Resource
* [Back to (predict) the future - Interactive M5 EDA](https://www.kaggle.com/headsortails/back-to-predict-the-future-interactive-m5-eda): The comprehensive visualisation of the data
* [M5 First Public Notebook Under 0.50](https://www.kaggle.com/kneroma/m5-first-public-notebook-under-0-50/): A very simple but elegant model that you could try. Don't forget to read the comments. There are ton of good intuition from the notebook's author and others.
* [Three shades of Dark](https://www.kaggle.com/c/m5-forecasting-accuracy/discussion/144067) A really long and great thought from Grandmaster Kaggler _Konstantin Yakovlev_




