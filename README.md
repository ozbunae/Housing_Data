# Phase 2 Project

## Project Description

Dave and Brenda are a young couple with hefty financial backing looking to purchase several properties and provide the manual labor to flip them into suitable Airbnb rentals.  They are unsure of where to buy, if it is even worth it to spend the time flipping a house, and what size house would be profitable?
For this project I used housing data from King County Washington combined with data from the Airbnb website to help make determinations 

### 1.1 The Data

This project uses the King County House Sales dataset, which can be found in  `kc_house_data.csv` in the data folder in this repo. The description of the column names can be found in `column_names.md` in the same folder. 

This project also utilized data that was parsed fromt the Airbnb website to Kaggle.  This information told us things like ratings, rental types, average nightly, monthly, and weekly cost, ext.  Although it weakened our model when we put it in it gave us a good idea of what the parameters were for the house type we were looking for.

### 1.2 Data Cleaning

As with all data we spent a lot of time cleaning the data.   The data really needed to be investigated by renovated v. non renovated.  The problem with this is that it divided up the data in a way that once it was cleaned created two very weak models.  Some useful information was retrieved from both of these scenarios but ultimately, a model with the data from both renovated v. non renovated homes was used.  

Histograms were used as a frequent technique through the cleaning process to see how normally distributed the continuous data was. The categorical data was binned and split into dummies in order to prevent it from messing with the final model.

For the main model with all of the original data, a z score multiplier was used to eliminate outliers.  Because it was such an agressive technique there was no need to go through the data column by column.  In the data sets separated by renovated v. nonrenovated, an interquartile method as well as individual column cleaning was applied in order to keep the smaller data frames in tact. 

### 1.3 Business Problem

The business problem is two young investors who want to invest in some homes to flip into Airbnbs.  Dave is a contracter and will do all of the work himself in order to elminate some overhead cost.  They want to know three things before they move forward with their descision:

1. Is it even worth it to renovate?  Is it possible to just find a home that is already renovated or in better condition to turn into an Airbnb?
2. If it is worth it, what areas should we be looking at?  Is there an opportunity to purchase a non renovated home next to an area that is already renovated?
3. What size home should you be buying?



## Exploratory Data Analysis

Exploratory Data Analysis shows us that 

### 2.1 Question 1:
We found that yes, it is definitely worth it to invest in a non renovated home if you are doing the renovations yourself.  
Investigating popular neighborhoods surrounding the already renovated areas to take advantage of prime real estate.  The mean cost of a grade 6 home from the renovated group of homes is on average $100,000 more than the average cost of a grade 6 non – renovated home.  This means that it seems to be significantly cheaper to purchase a property that has not been renovated and purchase materials to customize it.

![newplot](/Images/newplot.png)

![newplot(1)](/Images/newplot(1).png)

### 2.2 Question 2:
Heat maps were createed based on zip code with both the Renovated and Non Renovated data frames.
We were able to see trending areas that had not been renovated yet but were surrounding renovated areas.  

![Not Renovated](/Images/Not Renovated.png)

![Renovated](/Images/Renovated.png)

### 2.3 Question 3:
Airbnb data was cleaned and filtered using the interquartile method on the monthly price column.  This created a reasonable range of homes of which to work in.  Outliers were removed from other categories and categorical columns were explored.  After doing this, it was determined that it would be suitable to purchase a detached house that was 2-6 bedrooms and 1 -3 bathrooms.  All of the homes in this data set also had a score of 92/100 or higher in the review ratings column.  

## Regression Modeling

### 3.1 Problems
A model was built out using soley the KC data set.  Separating out the data into renovated and non renovated data and then building 2 seperate models resulted in an exceptionally low R2 and high p values. Adding in the Airbnb data set to the KC data set resulted in the same problem

### 3.2 Solution
A final regression model was built using only the KC data set.  The time of year and a few other variables were dropped from the beginning.  As an agressive approach to outliers, the z score method was used in the coding.  This took out the yr_renovated variable, but plenty of further analysis was done on this column.  After outliers removed, the data was listed by categorical and continuous variables.  Histograms were used to check for a normal distribution in continuous columns.  Bins were created for 3 of the categorical columns and then all categorical columns were ran with dummy variables.  

### 3.3 Checks and Balances
Several tests were performed to ensure that the model was refined as much as possible.

Tests include:

Variance of error
Breusch Pagan
QQ plot
Test and Train
Dropping one column from each set of dummies to keep our model in check

## Further Work

Exploring the Airbnb data even more and looking into world-wide trends with Airbnb data and not just King county.

Building a new model that takes into consideration the world-wide Airbnb trends.

Investigating specific zip codes that could ensure a high ROI.  And building new data sets that are customized to those zip codes.  I.e. what areas are trending both on the housing market as well as the Airbnb market. 

Examining the cost of materials to ensure that even with free labor there would still be a high ROI.


## Summary

Seeing that this young couple would like to do all of the renovations themselves,  it would definitely be worth it to purchase non renovated homes and flip them into custom Airbnbs.

You should purchase a home in the 'red' zone zip codes that are neighboring the currently renovated areas.

The home should be between 2 and 6 bedrooms 1 and 3 bathrooms and it should be a detached home.