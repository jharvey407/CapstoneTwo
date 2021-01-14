# Can We Identify Patients at High Risk 
# of Heart Failure with Machine Learning
***
Heart failure is a common event caused by cardiovascular disease. Cardiovascular diseases (CVDs) are the number 1 cause of death globally, taking an estimated 17.9 million lives each year, which accounts for 31% of all deaths worlwide.  
  
We used a dataset of 12 features that contribute to CVDs to predict mortality by heart failure.  
  
To view this project, click here: [Heart Failure Prediction](https://github.com/jharvey407/Heart_Failure_Prediction/blob/master/Heart%20Failure%20Profiling.ipynb)
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
  Death Event - boolean - whether or not the patient died during the course of the study.
  
## 2. Data Cleaning
Our dataset was very clean and well organized. There were no missing values and all values were either int64 or float64.  
There were 299 sets of 12 features and 1 target variable.  

Of the 299 patients, 96 have died of heart failure.

## 3. EDA
## 3.1 We used a combination of violin and box plots to get an idea of the distribution of our data and to look for outliers.
![serum creatinine and death](/graphics/AssociationOfSerumCreatinineAndDeath.png)
## 3.2 We used histograms to get an idea of the distribution of our target variable.  
![dist of age at death](/graphics/DistOfAgeAtDeath.png)  
## 3.3 We used Seaborn's PaitPlot to look for correlations in our data.  
![pair plot](/graphics/PairPlot.png)  
## 3.4 We also plotted linear regressions of individual feature correlations so that we could understand feature interaction.  
![correlation](/graphics/CorrelationEjectionFractionAndSerumSodium.png)  
## 4. Machine Learning Models  
We ran the following machine learning models and used metrics such as F1 Score and Balanced Accuracy to compare results. We also plotted Confuson Matrices of our classifiers.  
![random forest](/graphics/RandomForestTunedCM.png)
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
  
#### 4.3.3 Confusion Matrix  
![random forest](/graphics/RandomForestTunedCM.png)  
  
## 5 Conclusion  
We have found that it is possible to predict heart failure in patients given the right information, specifically __Ejection Fraction and Serum Creatinine__.  
***
### 5.1 Correlation Between Ejection Fraction and Serum Creatinine
![Entropy Tree](/graphics/CorrelationEjectionFractionAndSerumCreatinine.png)  
  1. In the above graph you can see a clear negative correlation between ejection fraction and mortality, meaning that the lower the ejection fraction, the more likely the patient is to suffer heart failure.
  2. In the above graph you can see a clear positive correlation between serum creatinine and mortality, meaning that the higher the serum creatinine, the more likely the patient is to suffer heart failure.
  3. In the above graph you can see by the clustering, that death event coincides wiht low ejection fraction and low serum creatinine, suggesting that ejection fraction is a more poweful indicator of possible heart failure, but the death events that coincide with a high serum creatine and high ejection factor suggest that high serum creatinine is also an indicator of possible heart failure.  
***
### 5.2 Reduction of False Negatives
We have also realized that it is important to focus on the elimination of __False Negatives__ in our modeling, following the logic that it is better to generate a false positive and conitnue follow-up with a healthy patient as opposed to genterating a false negative and not following up with an unhealthy patient.  
  
![random forest](/graphics/CMLowFN.png)  
The above confusion matrix shows that out of 99 predictions, we predicted only 8 false negatives, showing a false negative rate of only 8%.  
## 6. Project Notebook  
To view this project, click here: [Heart Failure Prediction](https://github.com/jharvey407/Heart_Failure_Prediction/blob/master/Heart%20Failure%20Profiling.ipynb)  
## 7. Further Reading  
The following similar study was conducted using the same data set, and reached the same conclusions regarding the prediction of heart failure.  
[Machine learning can predict survival of patients with heart failure from serum creatinine and ejection fraction alone](https://bmcmedinformdecismak.biomedcentral.com/articles/10.1186/s12911-020-1023-5#Sec6)
