# Titanic

## EDA:
  To understand the dataset better, we did Exploratory Data Analysis using pandas.
  ### Observations:
  ### Inferences and consequent Steps:

## Data Selection:
  ### Features we have selected: 
    1. age
    2. sex
    3. pclass
    4. sibsp (Siblings and Spouses)
    6. parch (Parents and Children)
    

##  Reasons why following features have been rejected:
    1. Cabin: While this has a pretty good Correlation Coefficient values (r), we have removed this feature to more nAn values
    2. PassengerId: Vey low value with respect to Survived
    3. Fare: Low r value corresponding to Survived
    4. Ticket: Low r value corresponding to Survived
    5. Name: Low r value corresponding to Survived
    6. Name_Title: This was originally created to contribute to the analyse the Survival rates of Nobility over the working class. r value corresponding to Survived
    7. Embarked: Low r value
