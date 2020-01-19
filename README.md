# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 2 - Ames Housing Data and Kaggle Challenge

## Table of Contents
- [Executive Summary](#Executive-Summary)
- [Introduction](#Introduction)
- [Problem Statement](#Problem-Statement)
- [Overview](#Overview)
- [Datasets](#Datasets)
- [Conclusion and Recommendations](#Conclusion-and-Recommendations)

--- 

### Executive Summary

The aim of this project is to build a regression model based on the Ames Housing Dataset of houses sold between year
 2006 and 2010 inclusive to predict the price of a house at sale and to investigate variables which have the greatest
  influence on the price of a house.  

Exploratory data analysis was first performed to investigate each predictor and target variable individually, and
 also to investigate pairwise relationships between all variables, both predictors and target variable. The rationale
  for exploratory data analysis was to investigate issues of multicollinearity and missing data and to effectively
   deal with them.
   
Thereafter, four linear regression models were built namely ordinary least squares linear regression, lasso
 regression, ridge regression, and elastic net regression. Cross-validation was performed to find the best
  hyperparameters for the regularized regression models and the root mean squared error was used as an evaluation
   metric to select the best model out of the four. The same steps were repeated to build another four linear
    regression models after feature engineering was performed to build regression models that had better predictive
     power.
     
 Lasso regression built on selected features, some of which were engineered, was selected as the best model as it had
  the lowest root mean square error. Total Square Foot of the house had the largest absolute coefficient in the model
   which suggests that it has the greatest influence on the Sale Price of a house. 

---

### Introduction

This project comprises predictive and inferential analysis of regression models built on the Ames Housing Data of
 houses sold between 2006 and 2010 inclusive. It studies and identifies trends in the housing data, and synthesizes information 
 from outside research with the data analysis. 
 In so doing, it aims to identify relevant features which could be used for building a regression model with good
  predictive power which has low bias and low variance. 
  Regression modeling was then performed with four different models namely ordinary least squares, lasso, ridge, and
   elastic net and it was found that the lasso regression model had the lowest root mean square error. It was also
    discovered that the total square foot of a house had the greatest influence on the price of a house.

---

### Problem Statement

To predict the sale price of a house in Ames, Iowa sold between 2006 and 2010 inclusive, and to identify the most
 influential factor on the sale price of a house in the same context.

---

### Overview

The pipeline:
- Data Cleaning
- Exploratory Data Analysis
- Data Visualization
- Descriptive and Inferential Statistics
- Pre-processing
- Modeling
- Outside Research
- Conclusions and Recommendations

---

### Datasets

#### Provided Data

For this project, there are four datasets provided:

- [Train Data](data/train.csv)
- [Train Data - Cleaned](data/train_cleaned.csv)
- [Test Data](data/test_data.csv)
- [Test Data - Cleaned](data/test_cleaned.csv)

The train data and test data were originally provided. They have been processed by converting the data types into the
 correct types (nominal, ordinal, discrete, continuous) and null values have been handled appropriately either by
  filling them with the correct value if the null values are meaningful or imputed if they are missing values.

#### Data Dictionary

|Feature|Type|Dataset|Description|
|:---|:---|:---|:---|
|**PID**|*category*|train, train_cleaned, test, test_cleaned|Parcel identification number  - can be used with city web site for parcel review|
|**MS SubClass**|*category*|train, train_cleaned, test, test_cleaned|Identifies the type of dwelling involved in the sale|
|**MS Zoning**|*category*|train, train_cleaned, test, test_cleaned|Identifies the general zoning classification of the sale|
|**Lot Frontage**|*float*|train, train_cleaned, test, test_cleaned|Linear feet of street connected to property|
|**Lot Area**|*float*|train, train_cleaned, test, test_cleaned|Lot size in square feet|
|**Street**|*category*|train, train_cleaned, test, test_cleaned|Type of road access to property|
|**Alley**|*category*|train, train_cleaned, test, test_cleaned|Type of alley access to property|
|**Lot Shape**|*int*|train, train_cleaned, test, test_cleaned|General shape of property|
|**Land Contour**|*category*|train, train_cleaned, test, test_cleaned|Flatness of the property|
|**Utilities**|*int*|train, train_cleaned, test, test_cleaned|Type of utilities available|
|**Lot Config**|*category*|train, train_cleaned, test, test_cleaned|Lot configuration|
|**Land Slope**|*int*|train, train_cleaned, test, test_cleaned|Slope of property|
|**Neighborhood**|*category*|train, train_cleaned, test, test_cleaned|Physical locations within Ames city limits|
|**Condition 1**|*category*|train, train_cleaned, test, test_cleaned|Proximity to various conditions|
|**Condition 2**|*category*|train, train_cleaned, test, test_cleaned|Proximity to various conditions (if more than one is present)|
|**Bldg Type**|*category*|train, train_cleaned, test, test_cleaned|Type of dwelling|
|**House Style**|*category*|train, train_cleaned, test, test_cleaned|Style of dwelling|
|**Overall Qual**|*int*|train, train_cleaned, test, test_cleaned|Rates the overall material and finish of the house|
|**Overall Cond**|*int*|train, train_cleaned, test, test_cleaned|Rates the overall condition of the house|
|**Year Built**|*int*|train, train_cleaned, test, test_cleaned|Original construction date|
|**Year Remod/Add**|*int*|train, train_cleaned, test, test_cleaned|Remodel date (same as construction date if no remodeling or additions)|
|**Roof Style**|*category*|train, train_cleaned, test, test_cleaned|Type of roof|
|**Roof Matl**|*category*|train, train_cleaned, test, test_cleaned|Roof material|
|**Exterior 1st**|*category*|train, train_cleaned, test, test_cleaned|Exterior covering on house|
|**Exterior 2nd**|*category*|train, train_cleaned, test, test_cleaned|Exterior covering on house (if more than one material)|
|**Mas Vnr Type**|*category*|train, train_cleaned, test, test_cleaned|Masonry veneer type|
|**Mas Vnr Area**|*float*|train, train_cleaned, test, test_cleaned|Masonry veneer area in square feet|
|**Exter Qual**|*int*|train, train_cleaned, test, test_cleaned|Evaluates the quality of the material on the exterior|
|**Exter Cond**|*int*|train, train_cleaned, test, test_cleaned|Evaluates the present condition of the material on the exterior|
|**Foundation**|*category*|train, train_cleaned, test, test_cleaned|Type of foundation|
|**Bsmt Qual**|*int*|train, train_cleaned, test, test_cleaned|Evaluates the height of the basement|
|**Bsmt Cond**|*int*|train, train_cleaned, test, test_cleaned|Evaluates the general condition of the basement|
|**Bsmt Exposure**|*int*|train, train_cleaned, test, test_cleaned|Refers to walkout or garden level walls|
|**BsmtFin Type 1**|*int*|train, train_cleaned, test, test_cleaned|Rating of basement finished area|
|**BsmtFin SF 1**|*float*|train, train_cleaned, test, test_cleaned|Type 1 finished square feet|
|**BsmtFin Type 2**|*int*|train, train_cleaned, test, test_cleaned|Rating of basement finished area (if multiple types)|
|**BsmtFin SF 2**|*float*|train, train_cleaned, test, test_cleaned|Type 2 finished square feet|
|**Bsmt Unf SF**|*float*|train, train_cleaned, test, test_cleaned|Unfinished square feet of basement area|
|**Total Bsmt SF**|*float*|train, train_cleaned, test, test_cleaned|Total square feet of basement area|
|**Heating**|*category*|train, train_cleaned, test, test_cleaned|Type of heating|
|**Heating QC**|*int*|train, train_cleaned, test, test_cleaned|Heating quality and condition|
|**Central Air**|*int*|train, train_cleaned, test, test_cleaned|Central air conditioning|
|**Electrical**|*int*|train, train_cleaned, test, test_cleaned|Electrical system|
|**1st Flr SF**|*float*|train, train_cleaned, test, test_cleaned|First Floor square feet|
|**2nd Flr SF**|*float*|train, train_cleaned, test, test_cleaned|Second floor square feet|
|**Low Qual Fin SF**|*float*|train, train_cleaned, test, test_cleaned|Low quality finished square feet (all floors)|
|**Gr Liv Area**|*float*|train, train_cleaned, test, test_cleaned|Above grade (ground) living area square feet|
|**Bsmt Full Bath**|*int*|train, train_cleaned, test, test_cleaned|Basement full bathrooms|
|**Bsmt Half Bath**|*int*|train, train_cleaned, test, test_cleaned|Basement half bathrooms|
|**Full Bath**|*int*|train, train_cleaned, test, test_cleaned|Full bathrooms above grade|
|**Half Bath**|*int*|train, train_cleaned, test, test_cleaned|Half baths above grade|
|**Bedroom AbvGr**|*int*|train, train_cleaned, test, test_cleaned|Bedrooms above grade (does NOT include basement bedrooms)|
|**Kitchen AbvGr**|*int*|train, train_cleaned, test, test_cleaned|Kitchens above grade|
|**Kitchen Qual**|*int*|train, train_cleaned, test, test_cleaned|Kitchen quality|
|**TotRms AbvGrd**|*int*|train, train_cleaned, test, test_cleaned|Total rooms above grade (does not include bathrooms)|
|**Functional**|*int*|train, train_cleaned, test, test_cleaned|Home functionality (Assume typical unless deductions are warranted)|
|**Fireplaces**|*int*|train, train_cleaned, test, test_cleaned|Number of fireplaces|
|**Fireplace Qu**|*int*|train, train_cleaned, test, test_cleaned|Fireplace quality|
|**Garage Type**|*category*|train, train_cleaned, test, test_cleaned|Garage location|
|**Garage Yr Blt**|*int*|train, train_cleaned, test, test_cleaned|Year garage was built|
|**Garage Finish**|*int*|train, train_cleaned, test, test_cleaned|Interior finish of the garage|
|**Garage Cars**|*int*|train, train_cleaned, test, test_cleaned|Size of garage in car capacity|
|**Garage Area**|*float*|train, train_cleaned, test, test_cleaned|Size of garage in square feet|
|**Garage Qual**|*int*|train, train_cleaned, test, test_cleaned|Garage quality|
|**Garage Cond**|*int*|train, train_cleaned, test, test_cleaned|Garage condition|
|**Paved Drive**|*int*|train, train_cleaned, test, test_cleaned|Paved driveway|
|**Wood Deck SF**|*float*|train, train_cleaned, test, test_cleaned|Wood deck area in square feet|
|**Open Porch SF**|*float*|train, train_cleaned, test, test_cleaned|Open porch area in square feet|
|**Enclosed Porch**|*float*|train, train_cleaned, test, test_cleaned|Enclosed porch area in square feet|
|**3Ssn Porch**|*float*|train, train_cleaned, test, test_cleaned|Three season porch area in square feet|
|**Screen Porch**|*float*|train, train_cleaned, test, test_cleaned|Screen porch area in square feet|
|**Pool Area**|*float*|train, train_cleaned, test, test_cleaned|Pool area in square feet|
|**Pool QC**|*int*|train, train_cleaned, test, test_cleaned|Pool quality|
|**Fence**|*int*|train, train_cleaned, test, test_cleaned|Fence quality|
|**Misc Feature**|*category*|train, train_cleaned, test, test_cleaned|Miscellaneous feature not covered in other categories|
|**Misc Val**|*float*|train, train_cleaned, test, test_cleaned|$Value of miscellaneous feature|
|**Mo Sold**|*category*|train, train_cleaned, test, test_cleaned|Month Sold (MM)|
|**Yr Sold**|*category*|train, train_cleaned, test, test_cleaned|Year Sold (YYYY)|
|**Sale Type**|*category*|train, train_cleaned, test, test_cleaned|Type of sale|
|**SalePrice**|*float*|train, train_cleaned|Sale price $$|

### Conclusion and Recommendations

Numeric and ordinal variables were selected in order of their individual correlation with the target variable
SalePrice, starting with the highest correlation. These variables were 
`Full Bath`, `TotRms AbvGrd`, `Garage Cars`, `Age`, `Mas Vnr Area`, `Gr Liv Area`,
`Garage Area`, `Total SF`, `Overall Qual`, `Exter Qual`, `Bsmt Qual`, `Kitchen Qual`,
`Fireplace Qu`, `Garage Finish`
 
`Age` removed as it presented problems of multicollinearity as it had a moderate correlation with each of the numeric
and ordinal variables.
  
Polynomial features of `Total SF`, `Gr Liv Area`, `Garage Area` raised to the power of 2 were engineered and added
to the model.
  
Nominal features were chosen based on their order of p-value, starting from the lowest: 
`Street`, `Foundation`, `Garage Type`, `MS Zoning`, `Central Air`, `Heating`, `Condition 2`, `Roof Matl` 
 
The final model which had the lowest RMSE was the Lasso regression model with the following variables:
`Bsmt Qual`, `Central Air_1`, `Condition 2_Feedr`, `Condition 2_PosA`,
`Condition 2_PosN`, `Condition 2_RRAe`, `Condition 2_RRAn`,
`Condition 2_RRNn`, `Exter Qual`, `Fireplace Qu`, `Foundation_PConc`,
`Foundation_Slab`, `Foundation_Stone`, `Foundation_Wood`, `Full Bath`,
`Garage Area`, `Garage Area^2`, `Garage Cars`, `Garage Finish`,
`Garage Type_Attchd`, `Garage Type_Basment`, `Garage Type_BuiltIn`,
`Garage Type_CarPort`, `Garage Type_Detchd`, `Garage Type_None`,
`Gr Liv Area^2`, `Heating_GasW`, `Heating_Grav`, `Heating_OthW`,
`Heating_Wall`, `Kitchen Qual`, `MS Zoning_C (all)`,
`MS Zoning_I (all)`, `MS Zoning_RH`, `MS Zoning_RL`, `MS Zoning_RM`,
`Mas Vnr Area`, `Overall Qual`, `Roof Matl_Membran`,
`Roof Matl_Tar&Grv`, `Roof Matl_WdShake`, `Roof Matl_WdShngl`,
`Street_Pave`, `Total SF`, `Total SF^2`
   
The coefficients of `Total SF`, and `Total SF^2` had the highest absolute values of all the chosen features which
 implied that `SalePrice` of a house is most heavily influenced by the size of the house.
 
Take note that this model may not necessarily be reliable when predicting sale price houses in other cities such as
 Los Angeles as buyers of houses in Los Angeles may not be as concerned about heating as they would houses in Ames
 , Iowa since the winters in Los Angeles are much milder than the winters in Ames. 
 
 Also, the model may be not be reliable when predicting sale prices of houses in Ames beyond the time period of 2006 and 2010
  , as there may be factors affecting house prices which are unaccounted for in the model such as political
   environment, interest rates, etc.