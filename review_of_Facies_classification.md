## Exploring the dataset
#### Data : facies_vector.csv
 
#### Columns

Facies|Formation|Well Name|Depth|GR|ILD_log10|DeltaPHI|PHIND|PE|NM_M|RELPOS
:---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---:
1 ~ 9| |Well name|Depth|Gamma ray|resistivity logging|neutron-density porosity difference| average neutron-density porosity| photoelectric effect | nonmarine-marine indicator | relative position

<br/>
These facies aren't discrete, and gradually blend into one another. Some have neighboring facies that are rather close. Mislabeling within these neighboring facies can be expected to occur. The following table lists the facies, their abbreviated labels and their approximate neighbors.


Facies |classes of rocks| Label| Adjacent Facies
:---: | :---: | :---: |:--:
1 |Nonmarine sandstone| SS| 2
2 |Nonmarine coarse siltstone| CSiS| 1,3
3 |Nonmarine fine siltstone| FSiS| 2
4 |Marine siltstone and shale| SiSh| 5
5 |Mudstone (limestone)| MS| 4,6
6 |Wackestone (limestone)| WS| 5,7
7 |Dolomite| D| 6,8
8 |Packstone-grainstone (limestone)| PS| 6,7,9
9 |Phylloid-algal bafflestone (limestone)| BS| 7,8

## About a method of training and Training the model

### Usage : SVM Classifier

#### Basic code for using SVM
```python
from sklearn import svm

clf = svm.SVC()
clf.fit(X_train,y_train)
predicted_labels = clf.predict(X_test)

from sklearn.metrics import confusion_matrix
from classification_utilities import display_cm, display_adj_cm
```

#### Confusion matrix
```python
conf = confusion_matrix(y_test, predicted_labels)
display_cm(conf, facies_labels, hide_zeros=True) %% 'display_cm' is given
```

#### Define accuracy and adjacent accuracy
```python
def accuracy(conf):
    total_correct = 0.
    nb_classes = conf.shape[0]
    for i in np.arange(0,nb_classes):
        total_correct += conf[i][i]
    acc = total_correct/sum(sum(conf))
    return acc
```

#### Model parameter selection
SVM using ```rbf``` kernel function has two parameters, c and gamma.
Tune these parameters using 'cross validation' method.

###### cross validation
>Two nested loops are used to train a classifier for every possible combination of values in the ranges specified. 

In this codes, ```C_range``` and ```gamma_range``` is following.
```
C_range = np.array([.01, 1, 5, 10, 20, 50, 100, 1000, 5000, 10000])
gamma_range = np.array([0.0001, 0.001, 0.01, 0.1, 1, 10])
```

We can get the proper parameters when the accuracy value is higest.
The value of ```gamma``` and ```C``` are 1 and 10 each in this codes.

#### Precision, Recall and F1 score
> Precision is the probability that given a classification result for a sample, the sample actually belongs to that class.</br> Recall is the probability that a sample will be correctly classified for a given class.

> F1 score combines both to give a single measure of relevancy of the classifier results.          

Precision and Recall can be computed using below function set ```display_metrics = True```.
```
display_cm(cv_conf, facies_labels, display_metrics=True, hide_zeros=True)
```
```
display_adj_cm(cv_conf, facies_labels, adjacent_facies, display_metrics=True, hide_zeros=True)
```
         
## Applying the model to the blind data

## Applying the model to new data

## Save the results
```python
well_data.to_csv('well_data_with_facies.csv')
```

