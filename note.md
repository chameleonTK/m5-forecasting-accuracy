
comments in 
https://www.kaggle.com/kneroma/m5-first-public-notebook-under-0-50/comments

lag_7: sales shifted 7 steps downwards for each group. The example above focuses on one group only as an example. That is why the first value appears on the 7th index.
lag_28: sales shifted 28 steps downwads. That is why the first value appears on the 28th index.
rmean_7_7: rolling mean sales of a window size of 7 over column lag_7. First value (0.2857) appears on the 13th index because means including nan are nan.
rmean_7_28: rolling mean sales of a window size of 7 over column lag_28. First value (0.357) appears on the 34th index because that is the first time the mean formula gets all 7 non-nan values.
rmean_28_7: rolling mean sales of a window size of 28 over column lag_7. First value (0.2857) appears on the 3th index because it is the first time the mean formula gets 28 non-nan values.
rmean_28_28: rolling mean sales of a window size of 28 over column lag_28. First value appears on 55th index because that is the first time the formula here all non-nan values.

The intuition as far as I can understand is the following:


1. Captures the week-on-week similarity and that too of just the past week. In other words, people are likely to shop this monday similar to the last monday (except it is some special occassion).
2. Captures the weekly similarity from a month-to-month perspective. Example: people in the 1st weekend of a month shop more so that weekend looks more similar to first weeks of other months than the previous weekend. (Though 28 is arguable here. A month is generally 30. Interesting would be a variable window depending on when the comparative week starts. Dealing with edge cases like week divided into 2 months will be tricky).

Since individual data points are prone to erratic spikes or troughs, mean provides a more "representative" picture.

3. Captures the information regarding the sales of the whole previous week ending 7 days in the past i.e. if we are at day 14, then the average is of sales from days 1-7 NOT days 7-14. This provides the information about the whole week and not just a single day sale comparison like lag_7 to bring the lag_7 value into "better weekly context".
4. Captures the information regarding the sales of the entire previous 4 weeks ending 7 days in the past i.e. if we are at day 35, then the average is sales from days 1-28.

5. Captures the information regarding the sales of the whole week ending 4 weeks ago i.e. if we are on day 35, then the average is of sales from day 1-7. (Assuming for simplicity the month is 28 days), this provides the information of not just a month-to-month comparison of the same day (day 7 of month one vs day 7 of month two), but the entire week leading up to day 7. Again the idea I believe is to capture the whole week and not just a single day sale comparison like lag_28 to bring the lag_28 value into "better weekly context".
6. Captures the information regarding the sales of the entire previous 4 weeks ending 4 weeks in the past i.e. if we are at day 56, then the average is of days 1-28. (Assuming for simplicity the month is 28 days), the idea again is to bring the point value of lag_28 into a better context (i.e. of day 28 when being compared to day 56) into a "better monthly context".

How would you "talk" about these features?


Hey let's see how the sales were last friday compared to this friday?
Hey let's see how the sales were first weekend of the last month compared to first weekend of this month?
May be comparing last saturday to this saturday is too specific. Week-on-week same day trends are more likely to be similar if the prior week went similar too. It would make sense to not just have the last saturday but also the mean of the whole week leading upto that day to give the model the "hint" how normal the whole week was.