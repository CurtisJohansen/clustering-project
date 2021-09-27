# Clustering Project - Zillow

### Project Objectives

- For this project you will continue working with the zillow dataset. Continue to use the 2017 properties and predictions data for single unit / single family homes

- In addition to continuing work on your previous project, you should incorporate clustering methodologies on this project

- Your audience for this project is a data science team. The presentation will consist of a notebook demo of the discoveries you made and work you have done related to uncovering what the drivers of the error in the zestimate

### Project Goals:

- Find drivers of logerror "Zillow Zestimate"
- (logerror = predicted sale value - actual sale value)
    
- Construct a model that helps us better predict logerror

## Project Summary

### Audience

Zillow Data Science team

### Project Deliverables

- A clearly named final notebook. This notebook will be what you present and should contain plenty of markdown documentation and cleaned up code.

- A README that explains what the project is, how to reproduce you work, and your notes from project planning.

- A Python module or modules that automate the data acquisistion and preparation process. These modules should be imported and used in your final notebook.

### Data Dictionary:

| Target          |                   Definition                        |Datatype |
|-----------------|-----------------------------------------------------|:-------:|
| logerror        | difference between actual value and predicted value | float64 | 


| Feature                    |             Definition              |Datatype |
|----------------------------|-------------------------------------|:-------:|
|parcelid                    |unique property id                   |int64    |
|bedrooms                    |number of bedrooms                   |int64    |
|bathrooms                   |number of bathrooms                  |float64  |
|total_sqft                  |total calculated square feet         |int64    |
|county_code                 |county code                          |int64    |
|latidude                    |latitude of home location            |int64    |
|longitude                   |longitude of home location           |int64    |
|lotsizesquarefeet           |total calculated square feet         |int64    |
|regionidzip                 |zip code of property                 |int64    |
|year_built                  |year the property was built          |int64    |
|structuretaxvaluedollarcnt  |value of structure                   |int64    |
|value_assessed              |value of entire property             |int64    |
|landtaxvaluedollarcnt       |value of land on which property sits |int64    |
|tax_amount                  |tax amount                           |int64    |
|transactiondate             |date property was purchased          |object   |
|county                      |engineered column- county name       |object   |
|property_age                |engineered column- age of property   |object   |


| propertyusetypeid   |    Definition                            |
|---------------------|:----------------------------------------:|
|261                  |Single Family Residential                 |
|262                  |Rural Residence                           |
|263                  |Mobile Home                               |
|264                  |Townhouse                                 |
|265                  |Cluster Home                              |
|268                  |Row House                                 |
|273                  |Bungalow                                  |
|274                  |Zero Lot Line                             |
|275                  |Manufactured, Modular, Prefabricated Homes|       
|276                  |Patio Home                                |
|279                  |Inferred Single Family Residential        |



## Hypothesis

### Hypothesis 1 

- Correlation Test (Square Feet vs Log error)
- alpha = .05
- Null Hypothesis: There is no correlation between log error and total square feet of the property
- Alterate Hypothesis: There is a correlation between log error and total square feet of the property

### Hypothesis 2

- Correlation Test (Property Age vs Log error)
- alpha = .05
- Null Hypothesis: There is no correlation between log error and property_age
- Alterate Hypothesis: There is a correlation between log error and property_age

### Hypothesis 3 

- Correlation Test (Longitude vs Log error)
- alpha = .05
- Null Hypothesis: There is no correlation between log error and longitude
- Alterate Hypothesis: There is a correlation between log error and longitude

### Hypothesis 4

- T-Test (Bedrooms vs Log error)
- alpha = .05
- Null Hypothesis: There is no relationship between log error and bedroom count
- Alterate Hypothesis: There is a relationship between log error and bedroom count

#### Takeaways from Hypothesis Testing:
- We reject the null hypothesis on all four hypothesis test.
- There are relationships between the features and log error

## Executive Summary - Conclusions & Next Steps


- We reject the null hypothesis on all four hypothesis test.

- There is a relationship between Square Feet, Bedrooms, Property Age, Longitude and the log error
 
- Found clusters between:
    - age of property and number of bedrooms
    - age of property and total square feet of the property
    - longitude and total square feet of the property

- 2nd degree Polynomial regression model performed best - Model Performs 1.4% better than the baseline

- I would like to find if there are better predictors of log error by creating more clusters

- I would like to improve models by trying different clusters/features and algorithms

- I would like to use a cluster as a feature in modeling, did not use this time


## Pipeline Stages Breakdown


### Acquire

- Data is collected from the codeup cloud database with an appropriate SQL query

- The wrangle.py contains fuctions to:

  - Sets up the connection to the MySQL database where the data is stored

  - Acquires the Zillow data according to a SQL statement

  - Caches the acquired data locally to speed up processing

###  Prepare  

- Column data types are appropriate for the data they contain

- Missing values are investigated and handled

- The wrangle.py contains fuctions to:
 
    - remove nulls in columns/rows
    
    - remove any duplicates
    
    - removes outliers
    
    - split the data into train, validate, test 
    
    - scale numeric data 

### Explore

- The interaction between independent variables and the target variable is explored using visualization and statistical testing

- Clustering is used to explore the data. A conclusion, supported by statistical testing and visualization, is drawn on whether or not the clusters are helpful/useful 

- At least 3 combinations of features for clustering should be tried

### Model 

- At least 4 different models are created and their performance is compared. 

- One model is the distinct combination of algorithm, hyperparameters, and features.

- Best practices on data splitting are followed

## Reproduce My Project

You will need your own env file with database credentials along with all the necessary files listed below to run my final project notebook.

- Read this README.md
- Download the wrangle.py, explore.py and final_report.ipynb files into your working directory
- Add your own env file to your directory. (user, password, host)
- Run the final_report.ipynb notebook
