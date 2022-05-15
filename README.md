# Cardiovascular-risk-prediction-classifier
Aim : To build a ML model that reports a cardiovascular risk.

#Project summary:

Yay! We have completed the project and the journey had been full of learning. Summarizing what we have achieved so far in this project, 
## 1. Data exploration
 * Starting from loading dataset, we got the first look at our dataset. We quickly dropped features like 'id' and 'education' which were irrelevent to the analysis. Also, we had two features in textual format, so we transformed them into the numerical format. 
 * We viewed statistics of the data and found that there are no duplicate rows, no mismatched rows, however, we do have missing values in the dataset. We calculated the % of missing content and find that ~9% of data is missing. For this project we decided to drop the missing rows.

> ### a. Data Visualization
> * There is an imbalance between the classes, class 1 has only 15.1% of the data. 
* Information on independent variables, features like 'age' and 'sysBP' showed class separation boundaries. While other numerical features had overlapping classes. 
* 'totChol' had few outliers which were inconsistent with the data, so we dropped those rows.
* Plotting Pearson - correlation matrix we found out that there is a strong relationship between 'sysBP' and 'diaBP'.

## 2. Feature engineering
* We combined sysBP and diaBP to get avgBP.
* We combined all of the history features namely BPMeds, prevalentHyp, prevalentStroke and diabetes to get disease_history.

##3.  Feature selection
* Using Boruta, a feature selection method, we picked 'age','cigsPerDay' 'totChol', 'sysBP', 'diaBP', 'BMI', 'heartRate', 'glucose' only these 8 features came out to be on top from the original dataset.
* 'avgBP' was selected over sysBP and diaBP and 'disease_history' was also selected since it has comparably strong correlation with the dependent variable.* Categories in disease_history was formed as separate dummy variables.

##4. Creating train and test dataset
* We have created three datasets, 
> X_train using train test split, X_tl using undersampling technique tomeklinks over X_train and X_smote using oversampling technique SMOTE. 

##5. Build various ML models
* Built naive bayes, logistic regression, support vector machine, random forest and XGBoost model using the 3 train datasets.
* Finding optimal hyperparameters for support vector machine and XGBoost using BayesSearchCV.
* On comparing all the models Logistic regression model built on top of original dataset gave best performance.

##6. Explaining the logistic regression model properties and performance statistics
* We found out that Logistic Regression model is performing the best with minimum roc_auc score of 0.68, accuracy of 0.66, recall of 0.69 and precision of 0.263. 
* Features that are helpful in predicting the class in decreasing order of their importance are, 
