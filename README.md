# Capstone_Project_1

The Capstone Project focuses on analyzing crime data from Los Angeles from 2010 to present. The data was obtained in csv and went through several pre-processing steps. 

## Datetime variables

First, the ‘time’ variables were combined and converted into datatime format variable: ‘Date_Occurred_Time_Occurred’. In addition several more datetime features were created: ‘Time Occurred’ (in hours:minutes:seconds), ‘Date Occurred’ (day:month:year), ‘Hour’ (in hours), and ‘Minute’ (in minutes). The ‘Hour’ and ‘Minute’ variables were then used to make the sin and cos versions of hours and minutes for machine learning purposes: ‘Hour_sin’, ‘Hour_cos’, ‘Min_sin’, ‘Min_cos’. In addition, a categorical variable for time of day was created: ‘Time Code’.   

## Missing values and irrelevant variables 

Variable ‘Weapon Description’ was missing more than 50% data and was, therefore, eliminated as a whole. Variables ‘Victim Sex’, ‘Victim Age’ and ‘Victim Descent’ had variable amount data missing that overall comprised about ¼ of total row-wise data. For data storytelling purposes, missing values for the listed 3 variables were replace with ‘Missing’ label. ‘Premise Description’ missing variables comprised less than 1% missing variables and therefore, those were easily dropped. 

## Additional feature engineering  

‘Crime Code Description’ variable was very segmented and was grouped together to form a more general variable ‘Crime’ which combined similar crimes like ‘Robbery’ and ‘Theft, Person’ together into a single category ‘Robbery and Theft’. Another variable ‘Crime Detailed’ was created adding back some information to the ‘Crime’ variable to be able to see more insight into the types of general labels (ex. the types of ‘Robbery and Theft’). 

## Yearly Crime Trends

Yearly crime trend was examined for all the districts contained in the dataset

![Figure 1](https://github.com/dariazhuk357/Capstone_Project_1/blob/master/Images/LA%20Crime%20Rate%20by%20District.png)

77th Street and Southwest districts were found to have the most crime in LA from 2010 to 2017 (2018 was omitted since it did not contain full year information). 

 

4 districts were particularly interesting, since they portrayed constant increase in crime from around 2013: ‘Newton’, ‘Olympic’, ‘Central’, ‘Hollenbeck’.Foothill district was interesting in terms of portraying a decrease in crime, but was ignored in further data exploration due to a comeback in crime after 2014. 

What kind of crimes populated those 4 districts? 
  

‘Robbery and Theft’ and ‘Assault’ were the biggest contributors for all the 4 districts, with ‘Sex-Related  Crime’ coming in third place. Moreover, the trend in ‘Robbery and Theft’ and ‘Assault’ crimes mimicked the overall crime rise, signifying that those two crime categories were the main drivers of crime rise. 

What were the main sub-categories of ‘Robbery and Theft’? Did some of them grow after 2013? 

 

 

 

 

All districts seemed to have an increase in ‘Theft/Burglary From a Vehicle’, but overall showed no specific crime rise in the sub-categories of ‘Robbery and Theft’. 

What about ‘Assault’? 
 

 
 

 


All four districts showed an increase in ‘Assault w/Deadly Weapon’ and ‘Rape and Sexual Assault/Battery’. 

Which premises were most affected by what crime? 

 

 

What times are peak times of crime for the 4 districts?

## EDA analysis 


Were open investigations correlated with crime rise??? 
 


What is the distribution of the ‘Victim Age’? Are younger or older people more affected? 

 

 

Younger people are affected by a wider variety of crimes but older people are more affected by ‘Robbery and Theft’. 

Are females more affected than males? 

 
Females are more affected by a wider amount of crime, while males are more affected by ‘Robbery and Theft’. 

## Machine Learning

Machine learning model was built to predict ‘Assault’ and ‘Robbery and Theft’ in the districts with rising crime: Hollenbeck, Central, Olympic, and Newton. 

Model was built on the following features: 
Crime               219521 non-null int64
Month_sin           219521 non-null float64
Month_cos           219521 non-null float64
Latitude            219521 non-null float64
Longitude           219521 non-null float64
Min_sin             219521 non-null float64
Min_cos             219521 non-null float64
Victim Age          219521 non-null float64
Hour_sin            219521 non-null float64
Hour_cos            219521 non-null float64
Victim Descent_-    219521 non-null uint8
Victim Descent_A    219521 non-null uint8
Victim Descent_B    219521 non-null uint8
Victim Descent_C    219521 non-null uint8
Victim Descent_D    219521 non-null uint8
Victim Descent_F    219521 non-null uint8
Victim Descent_G    219521 non-null uint8
Victim Descent_H    219521 non-null uint8
Victim Descent_I    219521 non-null uint8
Victim Descent_J    219521 non-null uint8
Victim Descent_K    219521 non-null uint8
Victim Descent_L    219521 non-null uint8
Victim Descent_O    219521 non-null uint8
Victim Descent_P    219521 non-null uint8
Victim Descent_S    219521 non-null uint8
Victim Descent_U    219521 non-null uint8
Victim Descent_V    219521 non-null uint8
Victim Descent_W    219521 non-null uint8
Victim Descent_X    219521 non-null uint8
Victim Descent_Z    219521 non-null uint8
Victim Sex_-        219521 non-null uint8
Victim Sex_F        219521 non-null uint8
Victim Sex_H        219521 non-null uint8
Victim Sex_M        219521 non-null uint8
Victim Sex_N        219521 non-null uint8
Victim Sex_X        219521 non-null uint8

Best model was XBClasssifier with accuracy of 72% 







ROC score 74 % 

 




