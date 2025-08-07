Titanic Survival Prediction: A Logistic Regression Project
🚢 Project Goal
The objective of this project is to follow a complete machine learning workflow to predict passenger survival from the Titanic disaster. This involves data cleaning, exploratory data analysis (EDA), feature engineering, and building a predictive classification model.

📊 Dataset
This project uses a dataset created by merging the test.csv and gender_submission.csv files from the Kaggle Titanic competition.

test.csv: Contains passenger features like age, class, and gender for a subset of passengers.

gender_submission.csv: A sample submission file where the Survived column is a pre-made prediction based on a simple rule: 1 (Survived) if female, 0 (Did Not Survive) if male.

This merged dataset contains 418 passenger records and is used for both training and testing the model.

📋 Data Cleaning & Preprocessing
The initial dataset required several cleaning and preprocessing steps:

Handled Missing Values:

Age: 86 missing values were filled with the median age.

Fare: 1 missing value was filled with the median fare.

Cabin: 327 missing values were too numerous to impute, so the column was dropped.

Feature Engineering: Two new features were created to better capture passenger context:

FamilySize: The sum of siblings/spouses (SibSp) and parents/children (Parch).

IsAlone: A binary flag indicating if the passenger was traveling alone.

Categorical Encoding: Text-based columns (Sex and Embarked) were converted into numerical format using one-hot encoding.

🤖 Modeling & Evaluation
A Logistic Regression model was trained to classify passengers as either surviving or not surviving. The model's performance on the test set yielded the following results:

Accuracy: 100%

Confusion Matrix:

[[50  0]
 [ 0 34]]
Classification Report:

              precision    recall  f1-score   support

           0       1.00      1.00      1.00        50
           1       1.00      1.00      1.00        34

    accuracy                           1.00        84
   macro avg       1.00      1.00      1.00        84
weighted avg       1.00      1.00      1.00        84
🎯 Analysis of the Perfect Score: Understanding Data Leakage
Achieving a 100% accuracy score on a predictive model is extremely rare and almost always indicates a problem with the data, known as data leakage.

In this project, the "perfect" score occurred because the target variable (Survived) was taken from the gender_submission.csv file. This file did not contain the actual historical outcomes. Instead, it was a simple prediction where survival was determined entirely by gender.

The machine learning model easily discovered this perfect, artificial correlation between the Sex feature and the Survived target, leading to a 100% score. This is a classic example of target leakage, where the prediction target is contaminated by information from the features.

While the project successfully demonstrates the workflow of data cleaning, feature engineering, and model building, the result serves as a critical lesson: always ensure your target variable is true, independent historical data and not derived from the features used for prediction.

🛠️ Tools Used
Language: Python

Libraries:

Pandas & NumPy (Data Manipulation)

Matplotlib & Seaborn (Data Visualization)

Scikit-learn (Logistic Regression Model)

Environment: Jupyter Notebook
