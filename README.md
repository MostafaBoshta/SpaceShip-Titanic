# SpaceShip Titanic.
## Problem Definition.
   Welcome to the year 2912, where your data science skills are needed to solve a cosmic mystery. We've received a transmission from four lightyears away and things aren't looking good.
   The Spaceship Titanic was an interstellar passenger liner launched a month ago. With almost 13,000 passengers on board, the vessel set out on its maiden voyage transporting emigrants from our solar system to three newly habitable exoplanets orbiting nearby stars.
   While rounding Alpha Centauri en route to its first destination—the torrid 55 Cancri E—the unwary Spaceship Titanic collided with a spacetime anomaly hidden within a dust cloud. Sadly, it met a similar fate as its namesake from 1000 years before.
   Though the ship stayed intact, almost half of the passengers were transported to an alternate dimension!
   To help rescue crews and retrieve the lost passengers, you are challenged to predict which passengers were transported by the anomaly using records recovered from the spaceship’s damaged computer system.
   Help save them and change history!.
   
## Data Description.
 - **PassengerId** - A unique Id for each passenger. Each Id takes the form gggg_pp where gggg indicates a group the passenger is travelling with and pp is their number within the group. People in a group are often family members, but not always.
 - **HomePlanet** - The planet the passenger departed from, typically their planet of permanent residence.
 - **CryoSleep** - Indicates whether the passenger elected to be put into suspended animation for the duration of the voyage. Passengers in cryosleep are confined to their cabins.
 - **Cabin** - The cabin number where the passenger is staying. Takes the form deck/num/side, where side can be either P for Port or S for Starboard.
 - **Destination** - The planet the passenger will be debarking to.
 - **Age** - The age of the passenger.
 - **VIP** - Whether the passenger has paid for special VIP service during the voyage.
 - **RoomService, FoodCourt, ShoppingMall, Spa, VRDeck** - Amount the passenger has billed at each of the Spaceship Titanic's many luxury amenities.
 - **Name** - The first and last names of the passenger.
 - **Transported** - Whether the passenger was transported to another dimension. This is the target, the column you are trying to predict.
 
## Exploratory Data Analysis (EDA).
 **I used a new method to explore the dataset called Profiling report. It's used to find the error in the data and a description of each column.**
 
 ![](https://miro.medium.com/max/720/1*ZkWNyuiG40yNYPMWg1kkKA.gif)
           
 **From the report I found that:**
   - **We Found 3 High Cardinality columns:**
      - PassengerId.
      - Cabin.
      - Name.
   - **A high Missing Values that we cannot drop.**

## Filtering & Cleaning Data:
      - **We have 3 High Cardinality columns:**
      - **PassengerId:** our idintfier so we can't do anything with this column.
      - **Cabin:** it's high because we it contains 3 informations deck/num/side so we have to split it to 3 columns deck , num , side and because num is unique we can cancel it so we have 2 new columns deck and side and get rid of cabin column.
      - **Name:** and we can rid of this column cause it won't be usefull to us.
   
   - **Dealing with Missing Values:**
      - **Age Column:** In Age column we filled the missing values with age.mean().
      - **In Other numerical columns:** We filled the missing values with zero.
      - **In Categorical columns:** We filled the missing values with 'Missing'.
  
  - **Normalizing Data:**
      - Extracting the PassengerId column cause we don't want to change anything in it.
      - Using get_dummies function to apply the onehotencoder method.
      - Adding the PassengerId column Again.   
      
## Machine Learning Algorithm:
   **In Machine Learning I used Random Forest Cassifier with estimators number 500  and random state of 42.
   I reached an accuracy of 79.3% on the training data.**
   
## Test File:
   **In Test file I used the same approach used in cleaning train data and then used the model to predict the state of the passenger.** 
