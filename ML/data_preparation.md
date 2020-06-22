## Data Preparation

### Feature selection & Engineering
- Requires good domain knowledge for this exercise

#### Discard irrelvent data
- Remove any data which is not relevent in predicting the required output. This information will not be used in training the model to save time and resource.
- Remove the feature which has same values in dataset, this will not help in prediction

#### Gaps and anamolies
- fill the missing values
- look for incorrect data like -ve values for height
- Remove the feature which has very low data, lot of data is missing

#### Merge or add new features
- Data which has corelation can be merged into same feature for e.g height and age can be merged as height/age
- Change the format of existing feature for eg date can be converted into epoch time or just hour of the day based on the data
- Standardize the data ranges accross the features


## Principal Component Analysis (Algorithm used in data pre processing step)
- PCA is an unsupervised machine learning model
- PC is often used as a data pre processing step
- Ther can be as many PC's as features or values
- PC1 and PC2 can be used to plat a 2D graph to show groups of features

## Missing and unbalanced data

### Missing
- Impute the data by taking mean of rest of the data
- Remove that row of missing data from data set
- If too many data is missing from one column (feature) then column can be removed

### Unbalanced
- Removing data which is not correct, this requires domain knowledge as data which does not look correct might be important for model training
- Try to work on real data, ask for more data if data is not enough for model training. For e.g if manufaturing defect of some parts is to be predicted then with few defects (may be one week data) will not be enough, need more data points for defect may be one year data.
- Oversample minority data. For e.g insert same defect data into dataset multiple times. But it might lead to model predicting only that type of fault
- Synthesize the data. Create more data with domain knowledge or talk to people involve in that process to change some features for creating defect data
- Try different algorithm type which is more suited for the type of data in hand

## Label and one hot encoding
Machine learning algorithms use numbers

### Label Encoding
- Encode the text values with numbers, and maintain a lookup table to reference them again for e.g Country

### One hot encoding
- Replacing the text with numbers can create ranking problem if numbers are choosen from 1 to n for categorical features
- To overcome this, create seperate feature for each country and put 1 if that country else out 0



