# TITANIC

## EDA:
  To understand the dataset better, we did an Exploratory Data Analysis using pandas and Numpy. 
  
  ### About the DataFrame:
    From that, we have observed that the Titanic train Dataset has a total of 891 rows and the test Dataset has a total of 418 rows. Each of the before mentioned Datasets initially have 6 dependent features (X) viz-a-viz PassengerId, Name,	Pclass,	Age,	SibSp,	Parch and	Fare. Additionally, the train Dataframe has the Independent Target (y) namely Survived. The train Dataset has a total of 899 values throughout the Dataframe. The test on the other hand has 414 null values. In order to avoid overfitting, bith train and test are maintained separetely.
  
  ### Handling Null data:
  
   ##### Exhibit A: Age - Continuous Value:
     Replacing Null with mean, because at null, the plot is more centre aligned
    
   ##### Exhibit B: Embark - Discrete value:
    Replacing Null with Top
    
   ##### Exhibit C: Cabin - Discrete value (Comes with a Catch):
    The problem with Cabin is the fact that it has way too many NaN values to the point it is the Top most value. 
    Ergo Cabin would eventually not be selected for the features.
  
  ### Deriving Features:
    There was a possibilty to derive the Cabin_Type, Name_Title, Family from Cabin and Name respectively. 
    
   #### Cabin_Type:
            1. Cabin_Type would simply take the alphabetical character at the start of the string.
            2. It would contribute to the Type of Cabin
            3. Cabin_Type has not been created in this solution because of the large volume of NaN values.
   
   #### Name_Title:
            1. It takes the honorific of a given name such as Mr. and Mrs.
            2. It is created to contribute to the analyse the Survival rates of Nobility over the working class.
            3. Name_Titles with same meanings (Mlle, Ms. and Mme., Mrs.) have been replaced with the commonly ocured Name_Title(Ms. an Mrs.)
  ##### Family: 
            1. It combines the values of Parch and SibSp to create a single attribute
            
## Plots:

  ### Sex vs Survived:
    Females have a higher Chance of Survival.
    
  ### Embarked vs Survived:
    There is not really much of a difference.
    But for the sake of quantifying this plot, it would be accurate to say that people who have embarked from place C have a better Survival Rate.
    
  ### SibSp vs Suvived: 
    SibSp is the abbreviated form of Sibling and Spouse.
    It was observed that Those with 1 Sibling or just their Spouse had a higher chance if Survival.
    
  ### Age vs Survived:
    Prople who were of ages 20-40 have a higher chance of Survuval
    
  ### Family vs Survived:
    Families with 3 members have the highest chances of survival
    
  ### Name_Title vs Survived:
     People with the Name_Titles: 'Sir', 'Countess' and 'Lady' have survived.
     Additionally, most of the people with the honorifics: 'Mrs', 'Ms', 'Master' have a higher Survival Rate
     Thus we infer that, Women, Children and Nobles have a higher Survival Rate
  
## Encoding:
    We have used an Ordinal Encoder to Encode Columns with String values. 
    The Columns encoded using an Ordinal Encoder are as follows:
      1. Embarked
      2. Sex
      3. Name_Title 
  
 ## HeatMap of the Correlation Coefficient:
    1. Correlation Coeeficient r between 2 items A and B states the quality of relationship between the two items A and B.
    2. HeatMap displays the correlation relationship between all items. 
    3. The strongest +ve relation is however within itself for every Feature.
    4. We use the Correlation to Select Features

## Features Selection:

  ### Selected: 
    1. Age
    2. Sex
    3. Pclass
    4. Family
    5. Embarked
    
##  Rejected:
    1. Cabin: While this has a pretty good Correlation Coefficient values (r), we have removed this feature to more nAn values
    2. PassengerId: Vey low value with respect to Survived
    3. Fare: Low r value corresponding to Survived
    4. Ticket: Low r value corresponding to Survived
    5. Name: Low r value corresponding to Survived
    6. Name_Title: Removed since the r value corresponding to Survived was lesser than expected
    7. SibSp: It is combined with Family
    8. Parch Adds wright to Family
    
## Check train and test once again:
    To check if the order and selection of train features and test features were the same. 
    When it was seen that they weren't, train features were switched to match test.

## Models and Observations:
  ### Random Forest Classifier:
  
   ##### Accuracy:
    1. Accuracy of RandomForest Model before Hyperparameter tuning with GridSearchCV is maintained at 80.8%
    2. But after Applying GridSearchCV, the Accuracy of RandomForest stands at 94.4%
    3. Best Parameters: Criteria: Entrophy, Max_Depth: 4, Max_Features: Auto, N_Estimator: 500
    4. Predict y for both cases.
    
   ##### Error Scores:
   
   Before HyperParameter Tuning:
   
      1. Error = |predicted values - actual values| (A matrix if 0 and 1)
      2. a) Mean Absolute Error = Sum of ((predicted value - observed value) ^2)/ n 
       b) Mean Absolute Error = 19.1%
      3. a) Root Mean Squared Error = Sum of (predicted value - observed value) / n 
       b) Root Mean Squared Error = 43.7%
      4. AUC value: 79.1
       
   After Hyper Parameter Tuning:
   
      1. Error = |predicted values - actual values| (A matrix if 0 and 1)
      2. a) Mean Absolute Error = Sum of ((predicted value - observed value) ^2)/ n 
       b) Mean Absolute Error = 5.5%
      3. a) Root Mean Squared Error = Sum of (predicted value - observed value) / n 
       b) Root Mean Squared Error = 23.4%
      4. AUC value: 93.7 
       
   ##### Confusion Matrix:
   
   Before Hyper Parameter Tuning:
   
      1. [[tp fp] [fn tn]]
      2. [[227 39][41 143]]
     
   After Hyper Parameter Tuning:
   
      1. [[tp fp] [fn tn]]
      2. [[257 9][14 138]]
    
   ##### Inference: 
    1. Accuracy Score of Random Forest Model is phenominally low. But After HyperParameterTuning GridSearchCV, the Accuracy score becomes higher. 
  
  ### Logistic Regression:
    
   ##### Accuracy:
    1. Accuracy Score of Logistic Regression: 94.0%.
    2. Accyracy Score of Logistic Regression after Hypyer Parameter Tuning stands at: 95.2%
    3. Predict y for both cases.
   ##### Error Scores:
   
   Before Hyperparemeter Tuning:
   
    1. Error = |predicted values - actual values| (A matrix if 0 and 1)
    2. a) Mean Absolute Error = Sum of ((predicted value - observed value) ^2)/ n 
       b) Mean Absolute Error = 5.9%
    3. a) Root Mean Squared Error = Sum of (predicted value - observed value) / n 
       b) Root Mean Squared Error = 24.4%
    4. AUC value: 93.7
    
   Afte Hyperparameter Tuning:
    
    1. Error = |predicted values - actual values| (A matrix if 0 and 1)
    2. a) Mean Absolute Error = Sum of ((predicted value - observed value) ^2)/ n 
       b) Mean Absolute Error = 4.7%
    3. a) Root Mean Squared Error = Sum of (predicted value - observed value) / n 
       b) Root Mean Squared Error = 21.8%
    4. AUC value: 92.9
   
   ##### Confusion Matrix:
   --- | ---
   Before Hyperparameter Tuning:| After Hyperparameter Tuning:
   --- | --- 
   1. [[tp fp] [fn tn]]| 1. [[tp fp] [fn tn]]
   --- | --- 
   2. [[252 14][11 141]]| 2. [[257 9][11 141]]
   --- | ---
   ##### Inference:
    1. There is no Huge difference of accuracy in Logistic Regression Before or After Hyper Parameter Tuning.
    2. However, Logistic Regression has a higher accuracy than Random Forest
    
  ### Naive Bayes Classifier:
  
   ##### Accuracy:
    1. Accuracy Score of Logistic Regression: 92.1%.
    2. Predict y
    
   ##### Error Scores:
    1. Error = |predicted values - actual values| (A matrix if 0 and 1)
    2. a) Mean Absolute Error = Sum of ((predicted value - observed value) ^2)/ n 
       b) Mean Absolute Error = 7.8%
    3. a) Root Mean Squared Error = Sum of (predicted value - observed value) / n 
       b) Root Mean Squared Error = 28.0%
    4. AUC value: 92.9
   
   ##### Confusion Matrix:
    1.  [[tp fp] [fn tn]]
    2. [[239  27] [6 146]]
    
   ##### Inference:
    1. Naive Bayes However has the lowest accuracy
   
 ## Conclusion:
    1.  Accuracy Score of Naive Bayes < Accuracy Score of Random Forest (After HyperParamter Tuning) < Accuracy Score of Logistic Regression (After HyperParameter Tuning).  
    2. While the error scores and accuracy scores are quite moderate, using Naive bayes isn't best practice 
    3. This is because it assumes that features are not correlated to eachother.
    4. However of the three above mentioned models, Logistic Regression has the highest accuracy.
   
 ## Model Selected based on the Above Mentioned Observations:
  #### Logistic Regression has the Highest Score! 
 
 ## Future Work:
    1. Hyperparameter Tuning in depth --Done for 2 models
    2. Grid Search -- Done for 2 models
    3. Gradient Boost
    4. Better EDA
      a) In depth analysis of Cabin feature to see if it can not be omiited simply because of NaN values
      b) Comparing Correlating attributes. For instance, finding which of the unmarried women who survived has at least one sibling who also survived.
      c) To avoid Overfit
    5. Model Testing
