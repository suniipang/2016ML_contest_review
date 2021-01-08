## Ensemble Method

1. Bagging
This algorithm generates multiple bootstrap training sets from the original training set and uses each of them to generate a classifier for inclusion in the ensemble. In general, bagging does more to **reduce the variance** in the base models **than the bias**, so bagging performs best relative to its base models when the base models have high variance and low bias. 

2. Boosting
This algorithm involves **incrementally** building an ensemble by training each new model instance to **emphasize the training instances that previous models mis-classified**. Boosting does more to **reduce bias than variance**. For this reason, boosting tends to improve upon its base models most when they have high bias and low variance.
However, this method of adjusting the training set distribution causes boosting to have difficulty when the training data are noisy. It is because the weights assigned to noisy examples often become much higher than for the other examples, often causing boosting to focus too much on those noisy examples and overfit the data 

<https://medium.com/@aravanshad/ensemble-methods-95533944783f>

## Random Forest vs Gradient Boosting Algorithm
GBM and RF differ in the way the trees are built: the order and the way the results are combined. It has been shown that GBM performs better than RF if parameters tuned carefully. 

### GBM
GBT build trees one at a time, where each new tree helps to correct errors made by previously trained tree.



### RF
RFs train each tree independently, using a random sample of the data. This randomness helps to make the model more robust than a single decision tree, and less likely to overfit on the training data


> Note: A very important point regarding how RF and GBM methods are *handling missing data*. Gradient Boosting Trees uses CART trees (in a standard setup, as it was proposed by its authors). CART trees are also used in Random Forests. CART handles missing values either by imputation with average, either by rough average/mode, either by an averaging/mode based on proximities. However, one can build a GBM or RF with other types of decision trees. The usual replacement for CART is **C4.5 proposed by Quinlan.** In C4.5 the missing values are not replaced on data set. Instead, the impurity function computed takes into account the missing values by penalizing the impurity score with the ratio of missing values.

<https://medium.com/@aravanshad/gradient-boosting-versus-random-forest-cfa3fa8f0d80>
