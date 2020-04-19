## directions
the challenge of this competition is the relationship between sales of days, we can have the following ways to explore the relationship -- 
1. how many years should be used in the training and testing -- would the past years be out of date due to the change of inflation;
2. how many days should be considered as an interval;
3. how can those categorical features affect the time interval -- 7-day interval may be better when we consider the mean of sale by categories (foods, hobbies, household)
4. the combination from the above fields

### General info
no nan is any columns (after melted the d_xx as 'd' and ‘sales’)

the range of sales is wide from 0 to 763 with mean 1.13 and std 3.87.

(to be continued)

### Category
FOODS        27489810 (47.13%)
HOUSEHOLD    20029110 (34.34%)
HOBBIES      10808450 (18.53%)

#### Range of sales in different categories (apporximately)
foods: mean is around 2.0, range is 0-2.5
household: mean is more than that of hobbies, around 0.6, range is 0-1.0
hobbies: mean is around 0.5, range is 0-0.6

from the graph with mean and std, we can see the std is big, meaning the sales in foods are discrete and needs to be further divided because the sales may vary in different areas, items and so on.


### Plan on the timeline
1. 19/04/2020 - 01/06/2020 (Full Training Labels Released): get the features and models done
    Goal: create or explore two models (one machine learning, the other one is deep learning), they may require different features
    1. 19/04 - 30/04: finish the exploration of data analysis and fix the number of years to be used in this competition
        exploration on the hold dataset might be too expensive, we could cut the size down first; identify the useful time period is also critical as it may change the values of each features
    2. 01/05 - 08/05: decide the number of days as the size of the window and the size of the stripe, and how to use the window (statistical way or just consider it as a feature -- this could be used in DL)
    3. 08/05 - 22/05: feature crossing: the effect of the categorical feature on the sales. E.g. which one/ones should use the statistical features on category/area/store/state
    4. 22/05 - 01/06: feature selection -- this actually could be done along the way of feature engineering, because we will put the features into the model to see the importance score for each feature. However, that one thing should be kept in mind is that even though a feature has a low score, you may not remove it, because the low-score feature may also have a positive effect on the accuracy.
2. 01/06/2020 - 30/06/2020 (Final submission deadline)
    1. fine-tune the model and keep feature engineering