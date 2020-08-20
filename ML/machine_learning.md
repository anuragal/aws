## Machine Learning

### Models

Regression Models 
1. Linear Regression - When prediction is a numeric value for e.g weight of the penguin 
    - Supervised
    - Used in forecasting
2. Logistic Regression - When prediction is either 1 or 0, yes or no for e.g patient will die or not
    - Supervised
    - This can be detected using Sigmoid function

Categorization Models
1. Support Vector Machines - Cluster information into categories
    - Supervised
    - Used for classification like customer classification (high value \ low value customer)
    - Choose support vectors on the edge of both the clusters, then draw a margin line for both clusters, then draw a hyperplane. Everything on either side of hyperplane is classified accordingly
2. Decison Trees
    - Supervised
    - Used for taking decisions based on
        - Binary Yes or No
        - Numeric 1,2,3
        - Classification
    - Decision tree also perform feature co-relation with entire dataset, whether that feature is anywhere related to required label

Random Forest
   - Supervised
   - Collection of decision trees
   - It picks the tree nodes at random and create nultiple decision trees with different nodes
   - output of every decision tree is used to predict the final output

K-means
    - Un-supervised
    - Classification
    - k is a number of data classes to be find
    - What is the best value of k?
        - This can be determine by plotting `reduction variation` vs `number of K graph`, on the graph at the point where `Elbow` is seen is the best value of K

K-Nearest Neighbour
    - Supervised
    - Classification
    - used for recommended engine
    - can be applied on the outcome of K-means algo
    - here K means the number of neighbours to be considered to classify a new point 
    
Latent Dirichlet allocation (LDA) algorithm
    - Un-supervised
    - Used for text analysis like word tagging, topic analysis
    - The aim of LDA is to find topics a document belongs to, based on the words in it
    - do the classification on the documents
    - Before analysis
        - Remove stop words like `and`, `to` etc
        - Apply Stemming to merge words like learn, learning & learnability
        - Tokenize, put all the words in array
    - Input to algo is number of topics
    

All models work on below principles
Data -> Algorithm -> Train -> Model -> Prediction
