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

ROC - 

AUC - 

![](https://github.com/anuragal/aws/blob/master/ML/ROC_AUC.png)
