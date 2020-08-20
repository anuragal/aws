## Deep Learning

The way our brain think and learn about verious things, similar way deep learning trying to learn and think.

Neurons

### Algorithms
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
