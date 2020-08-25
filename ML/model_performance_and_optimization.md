## Model Performance & Optimization
These tools help us understand the testing output from an ML model. They are a cornerstone for making further calculations

#### Confusion Matrix
A confusion matrix is a table that is often used to describe the performance of a classification model (or “classifier”) on a set of test data for which the true values are known. It allows the visualization of the performance of an algorithm

```
                                                   **Known Truth**
                                    
                                         Likes Dogs             Likes Cats(Does Not like dogs)

Model Predcition       Likes Dogs       TRUE POSITIVE                 FALSE POSITIVES
                                        (prediction is             (They actually like cats
                                         correct)                  but actually dont like dogs)

      
                       Likes Cats       FALSE NEGATIVE               TRUE Negatives
                       (Does not        (They actually like           (They dont like cats 
                        like cats)       dogs but predicted           and also predicted 
                                         they dont like dogs)         they dont like cats)
```

### Sensitivity & Specificity
Way to calculate how effective the model is by applying the confusion matrix values in the below formula

Sensitivity is a number of correct positive out of the actual positives results. It is also called as 
  - True Positive Rate
  - Recall
  
  Sensitivity = True Positives / (True Positives + False Negatives)
  
Specificity is a number of correct negative out of the actual negative results. It is also called as
  - True Negative Rate
  
  Sensitivity = True Negatives / (True Negatives + False Positives)
  
#### Examples 

Sensitivity - When bank wants to find all fraudalant transactions, in that process even if some false positive (legimitate transactions are flagged as fraud) cases are also picked up, that is fine. 

Speciticity - When parent wants to pick only those videos for kid that are age appropriate not the other ones, in that process even if some of the valid videos are left out, that is fine.


### Accuracy & Precision

Accuracy - The proportion of all the predictions which were correctly identified
  - How right was the model
  
    accuracy = (True Postives + True Negatives) / Total

Precision - The proportion of actual positives which were correctly identified
  - How right was the model in identifying the postive results
  
   precision = (True Postives) / (True Postives + False Positives)
   
### ROC/AUC

In a previous lesson we looked at the sensitivity and specificity of a machine learning model. But how far should we take this? When does a model become so sensitive that it's usless? ROC helps us determine the answer to this question, and AUC will help us see which model seperates our classes the best

In Machine Learning, performance measurement is an essential task. So when it comes to a classification problem, we can count on an AUC - ROC Curve. When we need to check or visualize the performance of the multi - class classification problem, we use AUC (Area Under The Curve) ROC (Receiver Operating Characteristics) curve. It is one of the most important evaluation metrics for checking any classification model’s performance. It is also written as AUROC (Area Under the Receiver Operating Characteristics)

![](https://github.com/anuragal/aws/blob/master/ML/ROC_AUC.png)

### Gini Impurity

How does a decision tree decide? Gini impurity is one of the calculations used to determine where to place nodes inside the tree

The Gini impurity measure is one of the methods used in decision tree algorithms to decide the optimal split from a root node, and subsequent splits. To put it into context, a decision tree is trying to create sequential questions such that it partitions the data into smaller groups. Once the partition is complete a predictive decision is made at this terminal node (based on a frequency). 

Suppose we have a list of observations, that indicates if a person decided to stay home from work. We also have two features, namely if they are sick and their temperature.

We need to choose which feature, emotion or temperature, to split the data on. A Gini Impurity measure will help us make this decision.

Def: Gini Impurity tells us what is the probability of misclassifying an observation.

Note that the lower the Gini the better the split. In other words the lower the likelihood of misclassification.

### F1 Score
Machine learning accuracy is sometimes not the best way to judge the effectivness of our model. F1 Score takes more into account and can be a better measure for models if we have an uneven class distribution

F1 Score = 2*( (precision*recall) / (precision+recall) ). 

It is also called the F Score or the F Measure. Put another way, the F1 score conveys the balance between the precision and the recall.
