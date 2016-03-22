#Titanic Survivors

##Given a list of passengers from the Titanic. You need to figure out and predict if the passener survived the disaster. The accuracy must beat 80%

Let's look at some assumptions. 
If you are rich you were higher up on the ship and had more access to the boats
If you were a female there was a gender bias towards you receiving access

Survivorship could be based on 

1. Gender
2. Fare price
3. Pclass (1 and 2)

Let's test this: 


First let's just run a predictor against women. 

Psuedo code: 

1. Lets make a passenger attributor that assumes they are all dead, then we can screen alives as we go
2. Establish all variables for each passenger
3. Establish an educated guess: First trial
	a. If a woman: You survived
4. If they survived, then change prediction score to yes (1) else give prediction score a no (0)

###Try 1


       `# Make everyone dead
        survived = False
        # Prediction model variables
        passenger_id = passenger["PassengerId"]
        sex = passenger["Sex"]
        pclass = passenger["Pclass"]
        age = passenger["Age"]
        sibsp = passenger["SibSp"]
        fare = passenger["Fare"]
        cabin = passenger["Cabin"] #too many NaN
        embarkPoint = passenger["Embarked"] #(C = Cherbourg; Q = Queenstown; S = Southampton)`


if a woman you survived:
`
if sex == 'female':
            survived = True
`

###4. If they survived, then change prediction score to yes, if not then no


        `if survived:
             predictions[passenger_id] = 1
        else:
             predictions[passenger_id] = 0
        return predictions`

####Trials

####Trial 1

`
if sex == 'female':
            survived = True
`
**Returned 78.86%**

####Trial 2
Let's go with women and upper class
`
if sex == 'female' and pclass <=1:
	survived = True
**returned 71.5%**

#### Trial 3
If you're a rich woman, middle class woman or a rich man
`
if sex == 'female' and pclass <=2:
	survived = True
elif sex =='male' and pclass <=1:
	survived = True
`

### Trial 15
Rich and upper class females
upper class males less than age of 9 and with 2 siblings or less
or if you were younger than 15 and had family

        `if sex == "female" and pclass <= 2:
             survived = True
        elif sex == "male" and pclass > 1 and age <= 9 and sibsp <= 2:
             survived = True
        if age <= 15 and sibsp <= 2 and parch <= 3:
            survived = True`
**RETURNED: 81.71%**




`import numpy
import pandas
import statsmodels.api as sm

def custom_heuristic(file_path):
    '''
    You are given a list of Titantic passengers and their associated
    information. More information about the data can be seen at the link below:
    http://www.kaggle.com/c/titanic-gettingStarted/data

    For this exercise, you need to write a custom heuristic that will take
    in some combination of the passenger's attributes and predict if the passenger
    survived the Titanic diaster.

    Can your custom heuristic beat 80% accuracy?
    
    The available attributes are:
    Pclass          Passenger Class
                    (1 = 1st; 2 = 2nd; 3 = 3rd)
    Name            Name
    Sex             Sex
    Age             Age
    SibSp           Number of Siblings/Spouses Aboard
    Parch           Number of Parents/Children Aboard
    Ticket          Ticket Number
    Fare            Passenger Fare
    Cabin           Cabin
    Embarked        Port of Embarkation
                    (C = Cherbourg; Q = Queenstown; S = Southampton)
                    
    SPECIAL NOTES:
    Pclass is a proxy for socioeconomic status (SES)
    1st ~ Upper; 2nd ~ Middle; 3rd ~ Lower

    Age is in years; fractional if age less than one
    If the age is estimated, it is in the form xx.5

    With respect to the family relation variables (i.e. SibSp and Parch)
    some relations were ignored. The following are the definitions used
    for SibSp and Parch.

    Sibling:  brother, sister, stepbrother, or stepsister of passenger aboard Titanic
    Spouse:   husband or wife of passenger aboard Titanic (mistresses and fiancees ignored)
    Parent:   mother or father of passenger aboard Titanic
    Child:    son, daughter, stepson, or stepdaughter of passenger aboard Titanic
    
    Write your prediction back into the "predictions" dictionary. The
    key of the dictionary should be the passenger's id (which can be accessed
    via passenger["PassengerId"]) and the associating value should be 1 if the
    passenger survvied or 0 otherwise. 

    For example, if a passenger is predicted to have survived:
    passenger_id = passenger['PassengerId']
    predictions[passenger_id] = 1

    And if a passenger is predicted to have perished in the disaster:
    passenger_id = passenger['PassengerId']
    predictions[passenger_id] = 0
    
    You can also look at the Titantic data that you will be working with
    at the link below:
    https://www.dropbox.com/s/r5f9aos8p9ri9sa/titanic_data.csv
    '''

    predictions = {}
    df = pandas.read_csv(file_path)
    for passenger_index, passenger in df.iterrows():
        #
        # your code here
        #
    return predictions
`