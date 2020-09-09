# Titanic

## EDA:
  To understand the dataset better, we did an Exploratory Data Analysis using pandas and Numpy. 
  
  ### About the DataFrame:
    From that, we have observed that the Titanic train Dataset has a total of 891 rows and the test Dataset has a total of 418 rows. Each of the before mentioned Datasets initially have 6 dependent features (X) viz-a-viz PassengerId, Name,	Pclass,	Age,	SibSp,	Parch and	Fare. Additionally, the train Dataframe has the Independent Target (y) namely Survived. The train Dataset has a total of 899 values throughout the Dataframe. The test on the other hand has 414 null values. 
  
  ### Handling Null data:
  
   ##### Exhibit A: Age - Continuous Value:
     Replacing Null with mean.
    
   ##### Exhibit B: Embark - Discrete value:
    Replacing Null with Top
    
   ##### Exhibit C: Cabin - Discrete value (Comes with a Catch):
    The problem with Cabin is the fact that it has way too many NaN values to the point it is the Top most value. Ergo Cabin would eventually not be selected for the features.
  
  ### Analysing Data:
    
    
## Data Selection:
  ### Features we have selected: 
    1. Age
    2. Sex
    3. Pclass
    4. Sibsp (Siblings and Spouses)
    6. Parch (Parents and Children)
    

##  Reasons why following features have been rejected:
    1. Cabin: While this has a pretty good Correlation Coefficient values (r), we have removed this feature to more nAn values
    2. PassengerId: Vey low value with respect to Survived
    3. Fare: Low r value corresponding to Survived
    4. Ticket: Low r value corresponding to Survived
    5. Name: Low r value corresponding to Survived
    6. Name_Title: This was originally created to contribute to the analyse the Survival rates of Nobility over the working class. r value corresponding to Survived
    7. Embarked: Low r value

## Models and Observations:
  ### Random Forest Classifier:
    1. No major accuracy change in accuracy for depth, hence it is maintained as None.
    2. At max_leaf = 2, accuracy: 88.5%
    3. At max_leaf = 3, accuracy: 98.8%
    4. At max_leaf = 10, accuracy: 93.7%
    5. Thus we can observe that accuracy diference between 2 to 3 (leaves) is close to 10.2%, while accuracy difference between 3 to 10 (leaves) is 5.1% approx.
    6. 
    
   ### Error Scores:
   ### Inference:
  ## Future Work:
    1. In depth Hyperparameter Tuning with the help of Grid Search
    2. Gradient Boost
    3. Better EDA.
    4. In depth analysis of Cabin feature to see if it can not be omiited simply because of NaN values
    5. 
