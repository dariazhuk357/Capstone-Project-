# Analyzing LA Crime Data 

This repository is focused on analyzing and digging into crime data in Los Angeles from 2010 to present, as well as building a machine learning model capable of classifying a crime based on crime occurance. The data and its full variable description was obtained in the csv format from [this link](https://data.lacity.org/A-Safe-City/Crime-Data-from-2010-to-Present/y8tr-7khq). The data is continuously updated, therefore, the dataframe that was obtained at the link at the time of the project can be also accessed in this repo in [Files](https://github.com/dariazhuk357/Capstone_Project_1/tree/master/Files). The data frame went through Data Cleanining and Feature Engineering steps. The process for Data Cleaning and Feature Engineering steps can be accessed in this repo in [Data Cleaning](https://github.com/dariazhuk357/Capstone_Project_1/tree/master/Data%20Cleaning) and [Feature Engineering](https://github.com/dariazhuk357/Capstone_Project_1/tree/master/Feature%20Engineering), respectively. The same folders can be used to access the resulting cleaned and engineered dataframes in a partioned format, ready for download. The following pre-processed, [final data frame](https://github.com/dariazhuk357/Capstone_Project_1/tree/master/Feature%20Engineering/Final_Partitioned_DataFrame) was used for [EDA](https://github.com/dariazhuk357/Capstone_Project_1/tree/master/EDA) and [Machine Learning](https://github.com/dariazhuk357/Capstone_Project_1/tree/master/Machine%20Learning) purposes described in detail below.   

# Data Cleaning and Exploration

Find the following work here [Data Cleaning](https://github.com/dariazhuk357/Capstone_Project_1/tree/master/Data%20Cleaning)

### Unnecessary variables 
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

### Missing values and irrelevant variables 

Variable ‘Weapon Description’ was missing more than 50% of the time, therefore, the variable was dropped completely.‘Premise Description’ missing values comprised less than 1% of the total dataframe were easily dropped. Variables ‘Victim Sex’, ‘Victim Age’ and ‘Victim Descent’ had variable amounts of data missing that overall comprised to approximately ¼ of total dataframe. For data storytelling purposes, the missing values for those 3 variables were replaced with a ‘Missing’ label.  

# Feature Engineering 

Find the following work here [Feature Engineering](https://github.com/dariazhuk357/Capstone_Project_1/tree/master/Feature%20Engineering)

### Datetime variables

The variables 'Date Occurred' and 'Time Occurred' in the original dataframe were parsed and combined into a datatime format variable: ‘Date_Occurred_Time_Occurred’. In addition several more datetime features were created: ‘Time Occurred’ (in hours:minutes:seconds), ‘Date Occurred’ (day:month:year), ‘Hour’ (in hours), and ‘Minute’ (in minutes). The ‘Hour’ and ‘Minute’ variables were then used to make the sin and cos versions of hours and minutes for machine learning purposes: ‘Hour_sin’, ‘Hour_cos’, ‘Min_sin’, ‘Min_cos’.    

### Additional feature engineering  

‘Crime Code Description’ variable was highly segmented with more than 140 unique labels and was,therefore, grouped together to form a more general variable ‘Crime’ which combined similar crimes like ‘Robbery’ and ‘Theft, Person’ together into a single category ‘Robbery and Theft’. Another variable ‘Crime Detailed’ was created by segmenting the ‘Crime’ variable for the insight into the types of general labels: eg. 'Robbery and Theft' was segmented into 'Grand Theft', 'Petty Theft' and etc. Automation of the creation of these variables was not possible due to extreme variability in the wording of the 'Crime Code Description' labels. Therefore, the variables were generated through using hardcoding techniques that would otherwise be avoided.   

# Exploratory Data Analysis 

Find the following work here [EDA](https://github.com/dariazhuk357/Capstone_Project_1/tree/master/EDA)
The dataframe used for this section can be found here: [final data frame](https://github.com/dariazhuk357/Capstone_Project_1/tree/master/Feature%20Engineering/Final_Partitioned_DataFrame).

The final cleaned and engineered dataframe contained the following variables with their descriptions: 

   - Date Occurred_Time Occurred - Time and date of crime occurance 
   - Area Name - District where crime occurred 
   - Crime Code Description - Crime label 
   - Victim Age - Age of the victim 
   - Victim Sex - Sex of the victim 
   - Victim Descent - Descent of the victim 
   - Premise Description - Description of the premise where the crime occurred 
   - Status Description - The status of the investigation on the crime 
   - Location - Longitude and Latitude coordinates of the crime location 
   - Date Occurred - Date of the crime occurrance 
   - Time Occurred - Time of the crime occurrance 
   - Hour - Hour of the crime occurrance 
   - Minute - Minute of the crime occurrance 
   - Day_of_Month - Day of the month of crime occurrance 
   - Month - Month of crime occurance 
   - Hour_sin - sin convertion of the hour of crime occurrance 
   - Hour_cos - cos convertion of the hour of crime occurrance 
   - Min_sin - sin convertion of the min of crime occurrance 
   - Min_cos - cos convertion of the min of crime occurrance 
   - Day_sin - sin convertion of the day of crime occurrance 
   - Day_cos - cos convertion of the day of crime occurrance 
   - Month_sin - sin convertion of the month of crime occurrance 
   - Month_cos - cos convertion of the month of crime occurrance 
   - Crime - Grouped, general version of 'Crime Code Description' (see Feature Engineering section for details)  
   - Crime_Detailed - Grouped, less general version of 'Crime' (see Feature Engineering section for details)  

### Yearly Crime Trends

Yearly crime trends were examined for all the districts contained in the dataset

![Figure 1](https://github.com/dariazhuk357/Capstone_Project_1/blob/master/Images/LA%20Crime%20Rate%20by%20District.png)

77th Street and Southwest districts were found to have the most crime in LA from 2010 to 2017 (2018 was omitted due to incompleteness). 

Additionally, 5 other districts (will be called 'focus districts' for the rest of this document) were particularly interesting. These districts portrayed a constant increase in crime starting from 2013: ‘Newton’, ‘Olympic’, ‘Central’, ‘Hollenbeck’, and 'Hollywood'. 'Foothill' district was interesting in terms of portraying a decrease in crime before 2014, but was ignored in further data exploration due to a spike in crime after 2014.

![Figure 2](https://github.com/dariazhuk357/Capstone_Project_1/blob/master/Images/Regions%20With%20Increasing%20and%20Decreasing%20Crime.png)

What kind of crimes populated focus districts? 
  
![Figure 3](https://github.com/dariazhuk357/Capstone_Project_1/blob/master/Images/Detailed%20Crime%20Count%202.png)

What kind of crimes populated the two most dangerous districts in LA? 

![Figure 4](https://github.com/dariazhuk357/Capstone_Project_1/blob/master/Images/Detailed%20Crime%20Count%201.png)

‘Robbery and Theft’ and ‘Assault’ were the biggest contributors in all focus districs, with ‘Sex-Related Crime’ in third place. Moreover, the trend in ‘Robbery and Theft’ and ‘Assault’ crimes mimicked the overall crime rise trend, signifying that those two crime categories could be the main drivers of crime rise. 

What were the main sub-categories of ‘Robbery and Theft’ in each of the focus districts? Crime in those districts began to spike after 2013. Did some of those sub-categories grow after 2013? 

All districts seemed to have an increase in ‘Theft/Burglary From a Vehicle’, but overall showed no specific crime rise in the sub-categories of ‘Robbery and Theft’. See the images here. 

What about ‘Assault’? 
 
**Central district, Assault - left (Before 2013), right (after 2013)**
![Figure 10](https://github.com/dariazhuk357/Capstone_Project_1/blob/master/Images/Central%20Assault%20Pie.png)
 
**Hollenbeck district, Assault - left (Before 2013), right (after 2013)**
![Figure 11](https://github.com/dariazhuk357/Capstone_Project_1/blob/master/Images/Hollenbeck%20Assault%20Pie.png)

**Newton district, Assault - left (Before 2013), right (after 2013)**
![Figure 12](https://github.com/dariazhuk357/Capstone_Project_1/blob/master/Images/Newton%20Assault%20Pie.png)

**Olympic district, Assault - left (Before 2013), right (after 2013)**
![Figure 13](https://github.com/dariazhuk357/Capstone_Project_1/blob/master/Images/Olympic%20Assault%20Pie.png)

**Hollywood district, Assault - left (Before 2013), right (after 2013)**
![Figure 14](https://github.com/dariazhuk357/Capstone_Project_1/blob/master/Images/Hollywood%20Assault%20Pie.png)

All five focus districts showed an increase in ‘Assault w/Deadly Weapon’ and ‘Rape and Sexual Assault/Battery’

The most dangerous districts (77th Street and Southwest) had a steady crime rate throughout the years. What were the sub-categories of 'Robbery and Theft' there?

**77th Street district, Robbery and Theft - left (Before 2013), right (after 2013)**
![Figure 15](https://github.com/dariazhuk357/Capstone_Project_1/blob/master/Images/77th%20Robbery%20Pie.png)

**Southwest district, Robbery and Theft - left (Before 2013), right (after 2013)**
![Figure 16](https://github.com/dariazhuk357/Capstone_Project_1/blob/master/Images/Southwest%20Robbery%20Pie.png)

What about 'Assault'?

**77th Street district, Assault - left (Before 2013), right (after 2013)**
![Figure 17](https://github.com/dariazhuk357/Capstone_Project_1/blob/master/Images/77th%20Assault%20Pie%20.png)

**Southwest district, Assault - left (Before 2013), right (after 2013)**
![Figure 18](https://github.com/dariazhuk357/Capstone_Project_1/blob/master/Images/Southwest%20Assault%20Pie%20.png) 

Which premises contained the most crime and what crimes affected them the most?

![Figure 16](https://github.com/dariazhuk357/Capstone_Project_1/blob/master/Images/Central%20Crime%20By%20Premise%20.png)

![Figure 18](https://github.com/dariazhuk357/Capstone_Project_1/blob/master/Images/Hollenbeck%20Crime%20By%20Premise%20.png)

![Figure 20](https://github.com/dariazhuk357/Capstone_Project_1/blob/master/Images/Newton%20Crime%20By%20Premise%20.png)

![Figure 22](https://github.com/dariazhuk357/Capstone_Project_1/blob/master/Images/Olympic%20Crime%20By%20Premise%20.png)

![Figure 24](https://github.com/dariazhuk357/Capstone_Project_1/blob/master/Images/Hollywood%20Crime%20By%20Premise%20.png)

What times are peak times of crime for the focus districts?

![Figure 25](https://github.com/dariazhuk357/Capstone_Project_1/blob/master/Images/Crime%20Daily%20Trend.png) 

From the above graph it can be seen that 12PM and 6PM-8PM are the peak crime times in almost all the focus districst and the two most dangerous districts in LA. 


## Machine Learning

Find the following work here [Machine Learning](https://github.com/dariazhuk357/Crime-in-Los-Angeles/blob/master/Machine%20Learning/Capstone_Project_1-Machine%20Learning%20.ipynb)
The dataframe used for this section can be found here: [final data frame](https://github.com/dariazhuk357/Capstone_Project_1/tree/master/Feature%20Engineering/Final_Partitioned_DataFrame).

Prior to building a machine learning model, missing variables in the 'Victim Sex', 'Victim Descent' and 'Victim Age' (previously labeled as 'Missing') were dropped. Additionally,'Victim Sex', 'Victim Descent' and 'Premise Description' variables were converted to categorical types.The 'Location' variable was split into two variables: 'Longitude' and 'Latitude'.

Additional EDA was performed in this section on 'Victim Age', 'Victim Sex', 'Minute', 'Hour' and 'Month' variables and can be viewed in the [Machine Learning](https://github.com/dariazhuk357/Crime-in-Los-Angeles/blob/master/Machine%20Learning/Capstone_Project_1-Machine%20Learning%20.ipynb) section notebook of this repository.

The based on EDA, the variables that were chosen to utilize for machine learning studies were: 

- Crime - classification label
- Latitude
- Longitude
- Min_sin
- Min_cos
- Victim Age
- Hour_sin
- Hour_cos
- Victim Sex - segmented into dummy variables 
- Victim Descent - segmented into dummy variables 

The dataframe for machine learning consisting of the above variables was limited to the 5 focus districs and the two most concerning crimes: 'Robbery and Theft' and 'Assault'. The unbalanced, binary variable 'Crime' was then balanced.

Multiple machine learning models were fit: DecisionTreeClassifier, ExtraTreesClassifier, MLPClassifier, AdaBoostClassifier, RandomForestClassifier, and XGBClassifier. Accuracies ranged from ~50-70 %. AdaBoostClassifier and XGBClassifier showed the best performance. XGBClassifier was chosen as the final model for the higher score in accuracy. Hyperparameter tunning resulted in the following parameters: 

- n_estimators: 40-150 (values from 40 to 150 yeilded essentially the same result) 
- max_depth: 10
- subsample: .8

The model with the stated parameters yeilded an ROC score of ~73 % with the the ROC curve below: 

![Figure 26](https://github.com/dariazhuk357/Crime-in-Los-Angeles/blob/master/Images/ROC%20curve%20.png)

To further imporve accuracy of the model addition of more descriptive features might be necessary. This can be accomplished by merging the original dataframe with additional datatables. This will be the future work. 






 




