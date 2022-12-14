# Credit_Risk_Analysis
Using Machine Learning algorithms to predict credit risk.

## Overview and Purpose
In this analysis, we aim to use machine learning algorithms to make predictions based off collected data. For this project, we were provided a dataset to evaluate lender's credit risk. Utilizing supervised learning models, we aim to predict whether lenders are at low or high risk based on a multitude of factors.

## Results
### Resampling Models
Before we can attain the desired results, we first needed to set the data up to be tested. We began by resampling the data using the scikit-learn and imbalanced-learn python libraries. As shown in the image below, the original dataset (after cleaning it to contain only the rows and columns needed for analysis) has a total of  68,817 applications grouped between low and high risk.

![](https://github.com/chichi-ugo/Credit_Risk_Analysis/blob/main/images/tot_values.PNG?raw=true)

This data is then split to create the models training and testing data

![](https://github.com/chichi-ugo/Credit_Risk_Analysis/blob/main/images/train_test_counts.PNG?raw=true)

**Oversampling**

To address the class imbalance, we see in the data, one of the methods used is a random oversampling model. In this model, instances of the minority class are randomly selected and added to the training set until the majority and minority classes are balanced. After resampling the data to increase the high-risk group to be even with the low risk, the results are as follows:

- *Balanced Accuracy Score* 
  - 66.1%
- *Precision Scores* 
  - High risk: 1%
  - Low risk: 100%
- *Recall Scores* 
  - High risk: 72%
  - Low risk: 60%
  
|                 |                   |
|-----------------|-------------------|
| ![O_Samp cm](https://github.com/chichi-ugo/Credit_Risk_Analysis/blob/main/images/naive_Osamp_cm.PNG?raw=true) | ![O_Samp class](https://github.com/chichi-ugo/Credit_Risk_Analysis/blob/main/images/naive_Osamp_class.PNG?raw=true) |


**SMOTE Oversampling**

Another resampling method we employed is SMOTE, or synthetic minority oversampling technique. In this method of oversampling, instead of just creating completely random data points, the model instead interpolates the data from the minority class and a number of their closest neighbors are chosen. Based on the values of these neighbors, new values are created. The results are as follows:

- *Balanced Accuracy Score* 
  - 65.8%
- *Precision Scores*
  - High risk: 1%
  - Low risk: 100%
- *Recall Scores*
  - High risk: 62%
  - Low risk: 69%
  
|                 |                   |
|-----------------|-------------------|
| ![SMOTE cm](https://github.com/chichi-ugo/Credit_Risk_Analysis/blob/main/images/smote_cm.PNG?raw=true) | ![SMOTE class](https://github.com/chichi-ugo/Credit_Risk_Analysis/blob/main/images/smote_class.PNG?raw=true) |


**Undersampling**

The third resampling method used in this analysis is the ClusterCentroids method of undersampling. In this model, the algorithm identifies clusters of the majority class, then generates synthetic data points, called centroids, which are representative of the clusters. The majority class is then undersampled down to the size of the minority class. The results from this resampling are as following:

- *Balanced Accuracy Score*
  - 54.4%
- *Precision Scores*
  - High risk: 1%
  - Low risk: 100%
- *Recall Scores*
  - High risk: 69%
  - Low risk: 40%
  
|                 |                   |
|-----------------|-------------------|
| ![U_Samp cm](https://github.com/chichi-ugo/Credit_Risk_Analysis/blob/main/images/Usamp_cm.PNG?raw=true) | ![U_Samp class](https://github.com/chichi-ugo/Credit_Risk_Analysis/blob/main/images/Usamp_class.PNG?raw=true) |


**Combination (Over and Under) Sampling**

The final resampling method that was employed in this analysis is SMOTEENN, a combination of combines the SMOTE and Edited Nearest Neighbors (ENN) algorithms. In this method, the minority class is oversampled using the SMOTE method and then  the data is cleaned using an undersampling strategy where if the two nearest neighbors are of a different class, the data is dropped. The results of this method are as follows:

- *Balanced Accuracy Score* 
  - 67.1%
- *Precision Scores*
  - High Risk: 1%
  - Low risk: 100%
- *Recall Scores*
  - High risk: 77% 
  - Low risk: 57%
  
|                 |                   |
|-----------------|-------------------|
| ![SMOTEENN cm](https://github.com/chichi-ugo/Credit_Risk_Analysis/blob/main/images/smoteenn_cm.PNG?raw=true) | ![SMOTEENN class](https://github.com/chichi-ugo/Credit_Risk_Analysis/blob/main/images/smoteenn_class.PNG?raw=true) |

### Ensemble Classifiers
The concept of ensemble learning is the process of combining multiple models, like decision tree algorithms, to help improve the accuracy and robustness, as well as decrease variance of the model, and therefore increase the overall performance of the model. In this analysis, we employed two ensemble classifier methods.

**Balanced Random Rainforest Classifier Model**

In the random forest method, the algorithm will sample the data and build several small, simple decision trees which are built from different subsets of features from the data. 

- *Balanced Accuracy Score* 
  - 78.9%
- *Precision Scores*
  - High Risk: 3%
  - Low risk: 100%
- *Recall Scores*
  - High risk: 70% 
  - Low risk: 87%
  
|                 |                   |
|-----------------|-------------------|
| ![BRRC cm](https://github.com/chichi-ugo/Credit_Risk_Analysis/blob/main/images/BRF_cm.PNG?raw=true) | ![BRRC class](https://github.com/chichi-ugo/Credit_Risk_Analysis/blob/main/images/BRF_class.PNG?raw=true) |

**Easy Ensemble Classifier Model**

- *Balanced Accuracy Score* 
  - 93.2%
- *Precision Scores*
  - High Risk: 9%
  - Low risk: 100%
- *Recall Scores*
  - High risk: 92% 
  - Low risk: 94%
  
|                 |                   |
|-----------------|-------------------|
| ![EEC cm](https://github.com/chichi-ugo/Credit_Risk_Analysis/blob/main/images/EE_cm.PNG?raw=true) | ![EEC class](https://github.com/chichi-ugo/Credit_Risk_Analysis/blob/main/images/EE_class.PNG?raw=true) |

## Summary
In comparing the six different models, we look specifically at the accuracy, precision, and sensitivity scores to distinguish which test may be more useful. The accuracy score assesses the performance of the model (a higher accuracy score indicates that the model is a better predictor). The precision score, also known as the positive predictive value (PPV), tells us the likelihood that the prediction made is True (Ratio of True positives to Total Positives - both true and false positives). Finally, the recall (sensitivity) score tells us the proportion of all True cases that are predicted by the model (ratio of predicted True positives to all actual positives - both true positives and false negatives).

Of all six models tested in this analysis, the EasyEnsembleClassifier model yielded the best results comparatively. The accuracy rating was the highest at 93.2%. It also yielded the highest precision score for predicting high risk cases at 9%. Finally, it has the highest sensitivity score for predicting high risk cases at 92%. In summation, of all the methods tested, it is recommended to use the EasyEnsembleClassifier.
