According to a study performed by Business Insider, Canada has been rated at # 6 as the safest country in the world in 2018. 
This makes Canada one of the most preferred country in the world for immigrants to come in and settle. 
I decided to take a deeper dive into this subject and further analyze the crime data within Canada to study how crime is 
placed across different provinces within Canada, what the general trend is in the last few years 
(is it on the rise or decreasing) and which province is the safest to live in. 
I have made an attempt to study the impact of the provincial spending in the education sector by the government of Canada 
on crime rate and have considered estimated population per province as a factor in my study. 
This report outlines all the steps I have gone through to conduct this comprehensive analysis and presented my findings.  
 


To be able to conduct this analysis, I selected the following 3 datasets: 

• Crime Dataset: Crime data from 1998 – 2016 in Canada (Total crime in Canada and per each province) 

• Education Dataset: Government of Canada expenditure on Education from 2008 – 2015 (Education expenditure per capita and education expenditure as % of GDP) 

• Population Dataset: Total estimated population from 1998 – 2016 (Total in Canada and per each province)  


Crime dataset
Following are the details of the quality of crime data and challenges. 
• Quality: The overall quality of this dataset is good.  
• Challenge: This dataset obtained was very large with more than 2M rows and 16 columns. The dataset was large because it contained data for various different type of violations. My target was to pick the total crime per province per year instead.  

The following steps were applied in cleaning and transforming this dataset: 
• Loaded the data into a data frame. 
• The following steps were applied in Python: 
     o Dropped all the different types of violations other than ‘Total, all violations’ and ‘Actual Incidents’ 
     o Dropped 13 out of 16 columns except the following 3: 
             ▪ REF_DATE which holds the Year 
             ▪ GEO which holds the name of the Province 
             ▪ VALUE which holds the number of crimes o Re-Indexed the filtered data set and renamed the columns as: 
             ▪ Year 
             ▪ Location
             ▪ Total_violations 
             
 
EDUCATION DATASET
2 Datasets for education data were obtained, both from statistics Canada website: 
1) Education expenditure per capita 
2) Education expenditure (as percentage of GDP) 
The 2 datasets were cleaned and merged. The dataset was available for the fiscal period of 2007/2008 – 2014/2015.

Following are the details of the quality of Education data per capita and % of GDP, and challenges. 
       • Quality: The overall quality of this dataset is good as its obtained from Stat Canada.  
       • Challenge: There were 2 different types of statistics in each dataset, the actual expenditure and the Index of change. I had drop the ‘Index of change’ as I only needed the expenditure.  
 
 The following steps were applied in cleaning and transforming this dataset: 
        • Loaded the data into a data frame. 
        • The following steps were applied in Python for ‘Expenditure per Capital’ Dataset 
                 o Dropped all the rows with statistics as ‘Index of Change’. Only kept the rows that specified ‘Expenditure per capita’. 
                 o Dropped 12 out of 15 columns except the following 3: 
                          ▪ REF_DATE which holds the Year 
                          ▪ GEO which holds the name of the Province 
                          ▪ VALUE which holds the expenditure o Re-Indexed the filtered data set and renamed the columns as: 
                          ▪ Year 
                          ▪ Location 
                          ▪ Expenditure_per_capital 
        • The following steps were applied in Python for ‘Expenditure as % of GDP’ Dataset 
                o Dropped all the rows with statistics as ‘Index of Change’. Only kept the rows that specified ‘Expenditure as percentage of gross domestic product’.
                o Dropped 12 out of 15 columns except the following 3: 
                          ▪ REF_DATE which holds the Year 
                          ▪ GEO which holds the name of the Province 
                          ▪ VALUE which holds the expenditure o Re-Indexed the filtered data set and renamed the columns as: 
                          ▪ Year 
                          ▪ Location 
                          ▪ Expenditure_as_percentage_of_GDP o Covered the Year column from fiscal year to calendar year. i.e. 2007/2008 was covered to 2008 and so on. 
                          
                          
 POPULATION DATASET 
The actual population data in Canada is obtained based on census that happens every few years. The last few Canadian population census happened in the years 2016, 2011, 2006 and 2001 when actual numbers were recorded.  
For my analysis, I required yearly population numbers per province so that I can analyze the crime rate per year per province factoring the population for each of those years. The dataset I used for this analysis are actual census numbers for the years census was conducted. The remaining years, the population numbers are estimated based on rate of increase of population in that province as per historic trend.

The following steps were applied in cleaning and transforming this dataset: 
             • Manually copied this dataset from pdf to a text file. The format of the dataset in the txt file was not structured. 
             • The following steps were applied in Python: 
                     o Parsing the dataset, removing unwanted characters, adding CRLR to split the dataset into multiple lines. 
                     o Space was use to split the data into individual columns. 
                     o Column names were updated matching the province names as in crime dataset and education dataset. 
                     o Transposing column dataset into rows to match in structure with other datasets.  
                     o Dropping data set from 1971 to 1998. 
 
 
