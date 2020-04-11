#### Idea about Minute 20200404
  1. Ways to do the project in a big picture
  * EDA + build by ourselves (prior)
  * learn the experiences from the others, especially about the features
    * from the baseline, I see he doesn't use the trend of sales from the files as a feature but group by
    id

2. Ideas of teamwork  
In the last competition, we split the fields of features to work parallelly. For example, I worked on the
trajectories and he worked on the feature crossing (distribution of one feature on another feature, like
speed on time). During the process, we kept exchanging experiences, like the boundaries of some features,
like the time, speed and so on. This worked fine.  
Therefore, I suggest we follow the above experience first to see how it goes for about two weeks.

3. Ideas of features and model   
In the last competition, in the feature engineering part, we didn't focus on the difference of rows, and 
maybe this is what I will work on first.
  * split the date based on a 7-day(could be 14/21/28) interval from Monday to see the pattern of sales
  on each Monday. That is because people may buy things for the whole week or certain intervals.
  * RNN counld be used here
(I should have learnt more about analysis on time-series data)
