# Titanic

## EDA:
  To understand the dataset better, we did an Exploratory Data Analysis using pandas and Numpy. 
  
  ### About the DataFrame:
    From that, we have observed that the Titanic train Dataset has a total of 891 rows and the test Dataset has a total of 418 rows. Each of the before mentioned Datasets initially have 6 dependent features (X) viz-a-viz PassengerId, Name,	Pclass,	Age,	SibSp,	Parch and	Fare. Additionally, the train Dataframe has the Independent Target (y) namely Survived. The train Dataset has a total of 899 values throughout the Dataframe. The test on the other hand has 414 null values. In order to avoid overfitting, bith train and test are maintained separetely.
  
  ### Handling Null data:
  
   ##### Exhibit A: Age - Continuous Value:
     Replacing Null with mean.
    
   ##### Exhibit B: Embark - Discrete value:
    Replacing Null with Top
    
   ##### Exhibit C: Cabin - Discrete value (Comes with a Catch):
    The problem with Cabin is the fact that it has way too many NaN values to the point it is the Top most value. 
    Ergo Cabin would eventually not be selected for the features.
  
  ### Derviving Features:
    There was a possibilty to derive the Cabin_Type and Name_Title from Cabin and Name respectively. 
    
   #### Cabin_Type:
            1. Cabin_Type would simply take the alphabetical character at the start of the string.
            2. It would contribute to the Type of Cabin
            3. Cabin_Type has not been created in this solution because of the large volume of NaN values.
   
   #### Name_Title:
            1. It takes the honorific of a given name such as Mr. and Mrs.
            2. It is created to contribute to the analyse the Survival rates of Nobility over the working class.
            3. Name_Titles with same meanings (Mlle, Ms. and Mme., Mrs.) have been replaced with the commonly ocured Name_Title(Ms. an Mrs.)
## Plots:

  ### Sex vs Survived:
    Females have a higher Chance of Survival.
    
  ### Embarked vs Survived:
    There is not really much of a difference.
    But for the sake of quantifying this plot, it would be accurate to say that people who have embarked from place C have a better Survival Rate.
    
  ### SibSp vs Suvived: 
    SibSp is the abbreviated form of Sibling and Spouse.
    It was observed that Those with 1 Sibling or just their Spouse had a higher chance if Survival.
    
  ### Name_Title vs Survived:
     People with the Name_Titles: 'Sir', 'Countess' and 'Lady' have survived.
     Additionally, most of the people with the honorifics: 'Mrs', 'Ms', 'Master' have a higher Survival Rate
     Thus we infer that, Women, Children and Nobles have a higher Survival Rate
     
## Encoding:
    We have used an Ordinal Encoder to Encode Columns with String values. 
    he Columns encoded using an Ordinal Encoder are as follows:
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
    4. Sibsp (Siblings and Spouses)
    6. Parch (Parents and Children)
    
##  Rejected:
    1. Cabin: While this has a pretty good Correlation Coefficient values (r), we have removed this feature to more nAn values
    2. PassengerId: Vey low value with respect to Survived
    3. Fare: Low r value corresponding to Survived
    4. Ticket: Low r value corresponding to Survived
    5. Name: Low r value corresponding to Survived
    6. Name_Title: Removed since the r value corresponding to Survived was lesser than expected
    7. Embarked: Low r value
    
## Check train and test once again:
    To check if the order and selection of train features and test features were the same. 
    When it was seen that they weren't, train features were switched to match test.

## Models and Observations:
  ### Random Forest Classifier:
  
   ##### Accuracy:
    1. At max_leaf = 2, accuracy: 88.5%
    2. At max_leaf = 3, accuracy: 98.8%
    3. At max_leaf = 10, accuracy: 93.7%
    4. Thus we can observe that:
      a) accuracy diference between 2 to 3 (leaves) is close to 10.2%
      b) accuracy difference between 3 to 10 (leaves) is 5.1% approx.
      Inference: For Different max_leaf values, accuracy differs.
    5. Find Optimum max_leaf, i.e max_leaf such thta it doesn't Overfit or Underfit the Data.
    6. For the train and test dataset, the Area under curve is a perfect fit. 
    7. We can thus obeserve that at and after the value of max_leaf value of 0.3, auc score is consistent.
    8. Intuitively, we can say that 0.3 is the threshold.
    9. Hence the accuracy Score is maintained at 63.6%.
    10. Predict y.
    
   ##### Error Scores:
    1. Error = |predicted values - actual values| (A matrix if 0 and 1)
    2. a) Mean Absolute Error = Sum of ((predicted value - observed value) ^2)/ n 
       b) Mean Absolute Error = 36.3%
    3. a) Root Mean Squared Error = Sum of (predicted value - observed value) / n 
       b) Root Mean Squared Error = 60.3%
    
   ##### Confusion Matrix:
    1. [[tp fp] [fn tn]]
    2. [[266 0][152 0]]
    
   ##### Inference: 
    1. Accuracy Score of Random Forest Model is phenominally low. 
  
  ### Logistic Regression:
  
   ##### Accuracy:
    1. Accuracy Score of Logistic Regression: 93.77%.
    2. Predict y.
   ##### Error Scores:
    1. Error = |predicted values - actual values| (A matrix if 0 and 1)
    2. a) Mean Absolute Error = Sum of ((predicted value - observed value) ^2)/ n 
       b) Mean Absolute Error = 6.2%
    3. a) Root Mean Squared Error = Sum of (predicted value - observed value) / n 
       b) Root Mean Squared Error = 24.9%
   
   ##### Confusion Matrix:
    1. [[tp fp] [fn tn]]
    2. [[252 14][12 140]]
   
   ##### Inference:
    1. Between Random Forest and Logistic Regression models, KLogistric Regression has  a higher score of accuracy
    2. This is because, Random Forest Model overfits.
    
  ### Naive Bayes Classifier:
  
   ##### Accuracy:
    1. Accuracy Score of Logistic Regression: 91.6%.
    2. Predict y
    
   ##### Error Scores:
    1. Error = |predicted values - actual values| (A matrix if 0 and 1)
    2. a) Mean Absolute Error = Sum of ((predicted value - observed value) ^2)/ n 
       b) Mean Absolute Error = 8.3%
    3. a) Root Mean Squared Error = Sum of (predicted value - observed value) / n 
       b) Root Mean Squared Error = 28.9%
   
   ##### Confusion Matrix:
    1.  [[tp fp] [fn tn]]
    2. [[237  29] [6 146]]
   ##### Inference:
    1. Naive Bayes However has a higher Accuracy than Random Forest, but lower Accuracy than Logistic Regression.
   
 ## Conclusion:
    1. Accuracy Score of Random Forest < Accuracy Score of Naive Bayes < Accuracy Score of Logistic Regression.  
    2. Due to Ovefit, there is a higher error rate and no false positives or false negatives.
    3. This would lead to errors if we were to apply this model for new data.
    4. While the error scores and accuracy scores are quite moderate, using Naive bayes isn't best practice 
    5. This is because it assumes that features are not correlated to eachother.
    6. However of the three above mentioned models, Logistic Regression has the highest accuracy.
    7. This is probably because, it doesn't overfit or Underfit and takes into consideration the corelation between attributes.
   
 ## Model Selected based on the Above Mentioned Observations:
  #### Logistic Regression has Higher Score!
 
 ## Future Work:
    1. Hyperparameter Tuning in depth
    2. Grid Search
    3. Gradient Boost
    4. Better EDA
      a) In depth analysis of Cabin feature to see if it can not be omiited simply because of NaN values
      b) Comparing Correlating attributes. For instance, finding which of the unmarried women who survived has at least one sibling who also survived.
    5. Select features for a specific threshold 
    6. Work Around for Chain Indexing
    7. Reduce Overfit in Random Forest Model 
       (Theoretically Overfit can be avoided by hyperparameter tuning of all parameters viz-a-viz depth, n-classifier, sample split and more.)
