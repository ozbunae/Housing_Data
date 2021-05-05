# Housing Data Project

## Project Description
For this project I used housing data from King County Washington which is the Seattle area. 
Moving on from basic EDA, this project centers around using linear regression and ordinary least squares methods to predict the price of housing data and find out what features have a large effect on the price of a home in this area.

### 1.1 The Data

This project uses the King County House Sales dataset, which can be found in  `kc_house_data.csv` in the data folder in this repo. The description of the column names can be found in `column_names.md` in the same folder. 

This project also utilized data that was parsed fromt the Airbnb website to Kaggle.  This information told us things like ratings, rental types, average nightly, monthly, and weekly cost, ext.  Although it weakened our model when we put it in it gave us a good idea of what the parameters were for the house type we were looking for.

### 1.2 Data Cleaning

As with all data we spent a lot of time cleaning the data.   The data really needed to be investigated by renovated v. non renovated.  The problem with this is that it divided up the data in a way that once it was cleaned created two very weak models.  Some useful information was retrieved from both of these scenarios but ultimately, a model with the data from both renovated v. non renovated homes was used.  

Histograms were used as a frequent technique through the cleaning process to see how normally distributed the continuous data was. The categorical data was binned and split into dummies in order to prevent it from messing with the final model.

For the main model with all of the original data, a z score multiplier was used to eliminate outliers.  Because it was such an agressive technique there was no need to go through the data column by column.  In the data sets separated by renovated v. nonrenovated, an interquartile method as well as individual column cleaning was applied in order to keep the smaller data frames in tact. 


## Exploratory Data Analysis

Exploratory Data Analysis was used to come up with some inital visualizations and answer preliminary questions in the process.

### 2.1 Question 1:
Yes, it is definitely worth it to invest in a non renovated home if you are doing the renovations yourself.  
Investigating popular neighborhoods surrounding the already renovated areas to take advantage of prime real estate.  The mean cost of a grade 6 home from the renovated group of homes is on average $100,000 more than the average cost of a grade 6 non – renovated home.  This means that it seems to be significantly cheaper to purchase a property that has not been renovated and purchase materials to customize it.

Not Renovated

![newplot](/Images/newplot.png)

Renovated

![newplot(1)](/Images/newplot(1).png)

### 2.2 Question 2:
Condition v. Grade of a Home.  This was a case where the question arose out of a graph that was created.
![condvgrade](/Images/pic1.png)

Looking at this, the grade of the home does not match the condition of the home by year:

"The tricky part is when style and tastes change over decades. A comparable with the typical décor from 1980 with the cream laminate cabinets with wood trim, which were in style at the time, is considered to be average construction quality. Based on today’s trends, these cabinets look very dated. They may still be in very good condition, but they are average quality(in our case grade). The quality(grade) rating doesn’t change over time. In contrast, condition may erode over time if not maintained." [1]

Lower grade or quality or a home in the 2000s can be accounted for the by the "McMansion boom".  The concept of creating slap together houses that are excessive in size and fit the trendiness of the time.  The amount of pre-1960s homes that have are in top condition but are considered out dated are very high.  

### 2.3 Question 3:
How do neighborhoods effect price.

Looking below, the visualizations speak for themselves.  The excerpts from the heat map in this project show the neighborhoods Renton and Bellevue and they match on the heat map what the box plots are telling us about the price of a home in those areas.

![hoodbarplt1](/Images/pic4.png)

![hoodbarplt2](/Images/pic2.png)

![hoodbarplt3](/Images/pic3.png)

## Regression Modeling

### 3.1 Problems
A model was built out using soley the KC data set.  Separating out the data into renovated and non renovated data and then building 2 seperate models resulted in an exceptionally low R2 and high p values. Adding in the Airbnb data set to the KC data set resulted in the same problem.

### 3.2 Solution
A final regression model was built using only the KC data set.  As an agressive approach to outliers, the z score method was used in the coding, this did knock our yr_renovated feature and the waterfront feature.  More analysis is done on renovated v. non renovated homes in two separate jupyter notebooks.  After outliers removed, the data was listed by categorical and continuous variables.  Histograms were used to check for a normal distribution in continuous columns.  Bins were created for 3 of the categorical columns and then all categorical columns were ran with dummy variables.  

### 3.3 Checks and Balances
Multiple methods were used to check assumptions. 

This includes:

Variance inflation factor
Breusch Pagan
QQ plot
Test and Train
Dropping one column from each set of dummies to keep our model in check
Doing a log transformation on Price

![QQPlot](/Images/pic5.png)

This QQplot shows us the residuals v the predicted.  It should hug the line a little bit more.  

![Histogram](/Images/pic6.png)

This histogram was created after the log function was applied to the price category in an effort to normalize the distribution.  We can see it did a pretty good job but still has a bit of a left skew.

## Further Work

Taking a further look into Renovated v. Non Renovated homes.  Unfortunately there was severe class imbalance on these records and it eleminated this feature from the project.  More data acquisition could be done on this feature combined with a bootstrapping technique of some sort.

Creating an analysis of features by neighborhood could offer insight into which specific neighborhoods would be best to invest in.

Machine Learning models can be implemented in the future for more precise predictions on what will effect the cost of a home. 


## Summary

Looking into non renovated v. renovated homes and what areas to purchase them in using machine learning would be a generalized next step.
As with any project, more data acquisition can always be done.  The more data that we have for some of the under represented features will allow us to make better and more accurate predictions.  


