# Analyzing LA Crime Data 

Th is repository is focused on analyzing and digging into crime data in Los Angeles from 2010 to present, as well as building a machine learning model capable of classifying a crime based on crime occurance. The data and its full variable description was obtained in the csv format from [this link](https://data.lacity.org/A-Safe-City/Crime-Data-from-2010-to-Present/y8tr-7khq). The data is continuously updated, therefore, the dataframe that was obtained at the link at the time of the project can be also accessed in this repo in [Files](https://github.com/dariazhuk357/Capstone_Project_1/tree/master/Files). The data frame went through Data Cleanining and Feature Engineering steps. The process for Data Cleaning and Feature Engineering steps can be accessed in this repo in [Data Cleaning](https://github.com/dariazhuk357/Capstone_Project_1/tree/master/Data%20Cleaning) and [Feature Engineering](https://github.com/dariazhuk357/Capstone_Project_1/tree/master/Feature%20Engineering), respectively. The same folders can be used to access the resulting cleaned and engineered dataframes in a partioned format, ready for download. The following pre-processed, [final data frame](https://github.com/dariazhuk357/Capstone_Project_1/tree/master/Feature%20Engineering/Final_Partitioned_DataFrame) was used for EDA and Machine Learning Purposes described in detail below.   

## Data Cleaning and Exploration
# Unnecessary variables 
The following variables were repeats of other variables or were deemed as unimportant for the purpose of this project and, therefore, dropped for simplicity and conciseness of the dataframe: 

- DR Number
- Date Reported
- Reporting District
- MO Codes
- Crime Code
- Area ID 
- Premise Code
- Weapon Used Code
- Status Code
- Crime Code 1, Crime Code 2, Crime Code 3, Crime Code 4 
- Address
- Cross Street

# Missing values and irrelevant variables 

Variable ‘Weapon Description’ was missing more than 50% of the time, therefore, the variable was dropped completely.‘Premise Description’ missing values comprised less than 1% of the total dataframe were easily dropped. Variables ‘Victim Sex’, ‘Victim Age’ and ‘Victim Descent’ had variable amounts of data missing that overall comprised to approximately ¼ of total dataframe. For data storytelling purposes, the missing values for those 3 variables were replaced with a ‘Missing’ label.  

## Feature Engineering 
# Datetime variables

The variables 'Date Occurred' and 'Time Occurred' in the original dataframe were parsed and combined into a datatime format variable: ‘Date_Occurred_Time_Occurred’. In addition several more datetime features were created: ‘Time Occurred’ (in hours:minutes:seconds), ‘Date Occurred’ (day:month:year), ‘Hour’ (in hours), and ‘Minute’ (in minutes). The ‘Hour’ and ‘Minute’ variables were then used to make the sin and cos versions of hours and minutes for machine learning purposes: ‘Hour_sin’, ‘Hour_cos’, ‘Min_sin’, ‘Min_cos’.    

# Additional feature engineering  

‘Crime Code Description’ variable was highly segmented with more than 140 unique labels and was,therefore, grouped together to form a more general variable ‘Crime’ which combined similar crimes like ‘Robbery’ and ‘Theft, Person’ together into a single category ‘Robbery and Theft’. Another variable ‘Crime Detailed’ was created by segmenting the ‘Crime’ variable for the insight into the types of general labels: eg. 'Robbery and Theft' was segmented into 'Grand Theft', 'Petty Theft' and etc. Automation of the creation of these variables was not possible due to extreme variability in the wording of the 'Crime Code Description' labels. Therefore, the variables were generated through using hardcoding techniques that would otherwise be avoided.   

## Yearly Crime Trends

Yearly crime trend was examined for all the districts contained in the dataset

![Figure 1](https://github.com/dariazhuk357/Capstone_Project_1/blob/master/Images/LA%20Crime%20Rate%20by%20District.png)

77th Street and Southwest districts were found to have the most crime in LA from 2010 to 2017 (2018 was omitted since it did not contain full year information). 

4 districts were particularly interesting, since they portrayed constant increase in crime from around 2013: ‘Newton’, ‘Olympic’, ‘Central’, ‘Hollenbeck’.Foothill district was interesting in terms of portraying a decrease in crime, but was ignored in further data exploration due to a comeback in crime after 2014. 


![Figure 1](https://github.com/dariazhuk357/Capstone_Project_1/blob/master/Images/Regions%20With%20Increasing%20and%20Decreasing%20Crime.png)

What kind of crimes populated those 4 districts? 
  
![Figure 1](https://github.com/dariazhuk357/Capstone_Project_1/blob/master/Images/Detailed%20Crime%20Count%202.png)

![Figure 1](https://github.com/dariazhuk357/Capstone_Project_1/blob/master/Images/Detailed%20Crime%20Count%201.png)

‘Robbery and Theft’ and ‘Assault’ were the biggest contributors for all the 4 districts, with ‘Sex-Related  Crime’ coming in third place. Moreover, the trend in ‘Robbery and Theft’ and ‘Assault’ crimes mimicked the overall crime rise, signifying that those two crime categories were the main drivers of crime rise. 

What were the main sub-categories of ‘Robbery and Theft’? Did some of them grow after 2013? 

![Figure 1](https://github.com/dariazhuk357/Capstone_Project_1/blob/master/Images/Central%20Robbery%20Pie.png)

![Figure 1](https://github.com/dariazhuk357/Capstone_Project_1/blob/master/Images/Central%20Assault%20Pie.png)

![Figure 1](https://github.com/dariazhuk357/Capstone_Project_1/blob/master/Images/Hollenbeck%20Robbery%20Pie.png)

![Figure 1](https://github.com/dariazhuk357/Capstone_Project_1/blob/master/Images/Hollenbeck%20Assault%20Pie.png)

![Figure 1](https://github.com/dariazhuk357/Capstone_Project_1/blob/master/Images/Newton%20Robbery%20Pie.png)

![Figure 1](https://github.com/dariazhuk357/Capstone_Project_1/blob/master/Images/Newton%20Assault%20Pie.png)

![Figure 1](https://github.com/dariazhuk357/Capstone_Project_1/blob/master/Images/Olympic%20Robbery%20Pie.png)

![Figure 1](https://github.com/dariazhuk357/Capstone_Project_1/blob/master/Images/Olympic%20Assault%20Pie.png)

![Figure 1](https://github.com/dariazhuk357/Capstone_Project_1/blob/master/Images/Hollywood%20Robbery%20Pie.png)

![Figure 1](https://github.com/dariazhuk357/Capstone_Project_1/blob/master/Images/Hollywood%20Assault%20Pie.png)



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

 




