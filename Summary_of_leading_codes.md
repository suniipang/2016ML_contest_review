1. Preprocessing

### - Feature Augmentation

Mostly used : Feature Window, Spatial Gradient   (from 'ISPL team')

filter(medfilt ...), polynomial features


### - Outlier Removal

Z-score, MAD(modified Z-score)

(only 'PA team' used)

### - Handling Missing data

for PE imputation

- NaN to 0 or mean value
- make_pipeline(... , ...)
- MLP Regressor
- PCA, TPOT

2. Train Model

Usually Scaling process is contained.

- Deep Neural Network, SVM
- Random Forest ```RandomForestClassifier```
- Gradient Boosting ```GradientBoostingClassifier```
- AdaBoost ```AdaBoostClassifier```
- XGBoost ```XGBClassifier```

To tune parameters, GridSearch is mostly used. (```GridSearchCV``` or test one by one)

(CrossValidation to validate the model is used only by 'LA team'.

3. Apply to Testdata

Scoring

- Deterministic score : F1 score of the result when applying the model to test well.
- Stochastic score : mean value of F1 scores when 100 random_seed is given.


## Further Idea

In the previous paper about gerating missing log, we can generate the missing well log data, even if the number of missing sensor is more than one. In this contest, the given data has missing only in PE sensor. How about expan