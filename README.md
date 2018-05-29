<H1 style="text-align: center;">Predicting Bike Shares In Washington D.C Using Linear Regression</H1>

<H3>Project Overview</H3>

<H4>Introduction</H4>

  There is a growing concern over shrinking public places and growing traffic on the roads. This causes commute times 
  to grow exponentialy. To tackle this problem more innovative methods are adapted like bike sharing. This project focuses 
  on bike sharing trends in Washington D.C during the years 2011-2012 and tries to predict the future usage.
  
<H3>Design Of The Study</H3>

  The project uses the dataset got from <a href="https://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset">UCI machine 
  learning repository.</a> The dataset has 16000 plus instances which tracks the bike share count for each hour through out 
  the years 2011 and 2012.
  
  A analysis on the dataset will be completed and a prediction model will be developed. Also we will suggest ideas for the 
  company to improve the business.
  
  The project is implemented using python and its libraries like numpy, pandas, matplotlib, seaborn, statsmodels and scikit learn.
  
 <H3>Data Description</H3>
 
  Each instance in the dataset represent's a hourly usage. There are 3 dependent variables namely total bike shares, registered
  bike shares and casual bike shares. The sum of registered and casual bike shares is always equal to the total bike shares.
  
  
  Below is the list of dependent and independent variables.
  
  - instant: record index
- dteday : date
- season : season (1:springer, 2:summer, 3:fall, 4:winter)
- yr : year (0: 2011, 1:2012)
- mnth : month ( 1 to 12)
- hr : hour (0 to 23)
- holiday : weather day is holiday or not (extracted from [Web Link])
- weekday : day of the week
- workingday : if day is neither weekend nor holiday is 1, otherwise is 0.
+ weathersit : 
- 1: Clear, Few clouds, Partly cloudy, Partly cloudy
- 2: Mist + Cloudy, Mist + Broken clouds, Mist + Few clouds, Mist
- 3: Light Snow, Light Rain + Thunderstorm + Scattered clouds, Light Rain + Scattered clouds
- 4: Heavy Rain + Ice Pallets + Thunderstorm + Mist, Snow + Fog
- temp : Normalized temperature in Celsius. The values are derived via (t-t_min)/(t_max-t_min), t_min=-8, t_max=+39 (only in hourly scale)
- atemp: Normalized feeling temperature in Celsius. The values are derived via (t-t_min)/(t_max-t_min), t_min=-16, t_max=+50 (only in hourly scale)
- hum: Normalized humidity. The values are divided to 100 (max)
- windspeed: Normalized wind speed. The values are divided to 67 (max)
- **casual: count of casual users**
- **registered: count of registered users**
- **cnt: count of total rental bikes including both casual and registered**

<H3>Procedure</H3>

<H4>Data Wrangling</H4>
   
   The data has no missing values or invalid values. The independent variables are normalised. The data in all the columns matches
   the expected expected data type for that particular column.
  
<H4>Preliminary Analysis</H4>

  Preliminary analysis was performed by analysing the various dependent variables and their relationship with the dependent 
  variables. 
  
  The temprature and shares have a linear relationship as shown below.
  
  <img src = "../Meta/TempVsBikeShares.png"/>
  
  
  Below are the findings.
  
  <ol>
<li> Most of the users are registered regular users.</li>
<li> There is a significant increase in users in 2012. This may be due to a good marketing strategy.</li>
<li> There is less usage during weekends.</li>
<li> There is less usage during the holidays.</li>
<li> The company has failed to attract casual users and tourists. The marketing strategy should also focus on this group which can boost the business in the coming years.</li>
<li> The summer and fall has higher usage than winter and spring.</li>
<li> The march month has the highest share of casual users. This is probably because of tourists or political gatherings.</li>
<li> The temperature has a linear relationship with the number of users.</li>
<li> There are almost no users during harsh weathers which is expected.</li>
<li> The humidity has a inverse relationship with the number of users.</li>
<li> The company can provide better support or equipments during the colder days to increase the number of users.</li>
<li> As few predictor variables have positive and negative relationships with the dependant variable, linear machine learning models can be used to solve the problem.
</ol>

<H4>Machine Learning</H4>

The findings from preliminary analysis clearly shows a linear relationship between the predictor and dependent variables. A linear
regression model is a perfect application for this problem.

The dataset was modified by converting the categorical columns into seperate columns for each each value.

A 70/30 train/test split was created.

Feature selection was done using scikit learn's inbuilt class selectKBest.

A pipeline was created which has feature selection step and the machine learning step. As the data is already normalised, no scaling
operation is required.

Three seperate linear models were built using the above pipeline to predict total bike shares, registered bike shares and casual
bike shares.

A 5 fold cross validation was performed.

The Total bike share model was successful with a train r2 score of **0.79** and test r2 score of **0.67** and the 
mean squared error of **10670**

The Total bike share model was successful with a train r2 score of **0.78** and test r2 score of **0.67** and the mean squared error 
of **7364**

The Total bike share model was successful with a train r2 score of **0.62** and test r2 score of **0.56** and the mean squared error 
of **1156**

<H3>Conclusion</H3>

The modern cities need to find innovative ecofriendly ways to get around the problems like polution, traffic and shrinking 
public spaces. The bike sharing idea is a convinient, cheap and ecofriendly solution for some of the problems. With the help of
data science we can help the companies involved in these ideas to understand the users better and therefore help them to 
create better business models to benefit all the stake holders.

From the above data, we can see that the casual users and tourists seem not to embrace the idea yet. The company has to reach out
to this population through better marketing strategies which will make the company more profitable and the users will be 
benefited in return.
