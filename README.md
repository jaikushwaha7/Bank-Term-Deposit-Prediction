
# Bank-Term-Deposit-Prediction

![alt-text](https://raw.githubusercontent.com/vgaurav3011/Bank-Term-Deposit-Prediction/master/images/dataset-card.jpg)

## What Worked and What did not?

- The data has many missing values, I tried different approaches for handling it,by studying distribution and value counts that led to substituting with mode for categorical variables, to using median for numerical variables, it failed to give a very optimal solution.
- Tried backward and forward filling instead then, which also worked well except did not meet the requirements for top model.
- Ironically, to my surprise, and another good takeaway was that the top model used zeros as the filler for missing values, instead of worrying too much about it, and it converged well on the model.

Moral: Sometimes we try too many complex ideas, but eventually a simple idea works out well too, will be trying out simple ideas first that may give better results!

- Further, I tried target encoding, which failed as we cannot see much of a correlation between the target and other variables, except for last contact duration.
- I also mapped the data manually in form of a self made label encoding that worked very well, but was not enough alone.
- Tried one hot encoding and a mix of label encoding that did not work very well, (used label encoding for variable with less values, while one hot encoding for categories with many values to balance it out), however it performed worse than label encoding alone or one hot encoding alone too.
- Eventually, the best idea was to keep it simple with a direct one hot encoding of the categories, and it performed decently well for the model.

Moral: Again, simple encoding ideas worked out more for this data, need not necessarily mean the same for other datasets.

- Tried hands with Logistic Regression that ended up with a 48 F1-Score, which is majorly due to a few categorical variables with multiple values that could not be handled well by the probabilistic nature of LR. 
- Naive Bayes fails on the same data, due to its nature of considering all features to be equally important (although that does help in preventing overfitting a bit).
- Random Forest Classifier also did not work very well (May have improved with a better grid search but I did not perform that due to time constraint and it already had not a very good performance comparatively).
- Decision Tree Classifier was pretty decent, not very well either and even plotted a threshold for the same, but moved on with performance issues again here!
- Tried XGBoost with stratified shuffle split but again it failed to a certain degree.
- The class imbalance of the target variable is huge, handled it with SMOTE to observe performance improvement in XGBoost going to nearly 61 F1-Score.
- Tried Catboost instead of XGboost and got better results, fine tuned it with Grid Search to get better parameters, however the results were not very improved.
- Gradient Boosting Classifier outperformed all of these, but was overfitting to some degree, so again performed optimal parameter search and this helped the model to gain significant improvement.
- Light GBM outperformed all with a threshold optimization at 0.26 for rounding off the final predictions, and gives best results.
