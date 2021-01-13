# Can We Identify Patients at High Risk 
# of Heart Failure with Machine Learning
***
Heart failure is a common event caused by cardiovascular disease. Cardiovascular diseases (CVDs) are the number 1 cause of death globally, taking an estimated 17.9 million lives each year, which accounts for 31% of all deaths worlwide.  
  
We used a dataset of 12 features that contribute to CVDs to predict mortality by heart failure.  
***
![Entropy Tree](/graphics/EntropyTree.png)
***  

## 1. Data  
### 1.1 We used a dataset with 12 features.  
  
  1. age in years from 40 to 95
  2. anaemia - boolean
  3. creatinine phosphokinase levels from 970 to 7,861
  4. diabetes - boolean
  5. ejection fraction percentage from 14 to 80
  6. high blood pressure - boolean
  7. platelet count from 97,804 to 850,000
  8. serum creatinine levels from 0.5 to 9.4
  9. serum sodium levels from 113 to 148
  10. sex - boolean - male/female
  11. smoking - boolean
  12. follow up time in days from first appointment
  
### 1.2 Target Variable
  Death Event - boolean
  
## 2. Data Cleaning
Our dataset was very clean and well organized. There were no missing values and all values were either int64 or float64.  
There were 299 sets of 12 features and 1 target variable.  

## 3. EDA
We used a combination of violin and box plots to get an idea of the distribution of our data and to look for outliers.
![serum creatinine and death](/graphics/AssociationOfSerumCreatinineAndDeath.png)
We used histograms to get an idea of the distribution of our target variable.  
![dist of age at death](/graphics/DistOfAgeAtDeath.png)  
We used Seaborn's PaitPlot to look for correlations in our data.  
![pair plot](/graphics/PairPlot.png)  
We also plotted linear regressions of individual feature correlations so that we could understand feature interaction.  
![correlation](/graphics/CorrelationEjectionFractionAndSerumSodium.png)  
## 4. Machine Learning Models  
We ran the following machine learning models and used metrics such as F1 Score and Balanced Accuracy to compare results. We also plotted Confuson Matrices of our classifiers.  
![random forest](/graphics/RandomForestTuned.png)
### 4.1 Machine Learning Models  
  1. Decision Tree Entropy Model
  2. Decision Tree Gini Model
  3. Random Forest Classifier
  
### 4.2 Feature Selection  
We used Recursive Feature Selection, Hyperparameter Tuning and Prinicple Component Analysis to indentify the most important features.  
In the end we used 2 important features, __Ejection Fraction and Serum Creatinine__.  

### 4.3 Model Selection  
After extensive testing we settled on the Random Forest model with 2 Prime Features and Tuned Hyperparameters.  
  
#### 4.3.1 Best Parameters  
  1. n_estimators: 1600
  2. min_samples_split: 10
  3. min_samples_leaf: 4
  4. max_features: sqrt
  5. max_depth: 30
  6. bootstrap: True
  
#### 4.3.2 Model Metrics
We acheived the follow results by averaging 100 interations of the Random Forest Model with the above hyperparameters.  
  1. Accuracy: 0.762
  2. Balanced Accuracy: 0.703
  3. F1 Score: 0.584
  4. Precision Score: 0.666
  5. Precision Score for Positive: 0.666
  6. Precision Score for Negative: 0.800
  7. Recall Score: 0.534
  8. Recall Score for Positive: 0.534
  9. Recall Score for Negative: 0.872
  
__Confusion Matrix__  
