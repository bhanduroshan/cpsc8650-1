# Introduction
In the recent decade, we have seen world being more and more industrialized. With industrialization, countries appear to produce more and more greenhouse gases. Global temperature is rising and rainfall id getting erratic, this is causing problems in different sectors of our society and the world. In this project we mine the climate change data set from the World Bank and analyze the cause, the effect and predict the future so that we can initiate mitigation steps for the problems caused by climate change. 

# Methodologies
We utilized data mining methodologies throughout the course of this project. This includes data extraction, data cleaning and formatting, generating basic stats followed by clustering and regression analysis.


# Cause Mining
To mine the climate change data and predict its effects in near future, we initially identify the relation of climate factors like temperature and rainfall with environmental factors such as CO2 emission. We believe identifying these relationships would provide a general view of the current environmental state which would then help analyze its effect on socio-economic factors. To mine the cause, we used data mining techniques listed below.

# Correlation Analysis 
Correlation Analysis is a statistical technique in which we evaluate the strength of relationship between quantitative variables. We loaded the dataset into pandas dataframe and then use panda's inbuilt function for calculating Perason's coefficient. Following code demonstrates how we implemented correlation analysis using Pearson's coefficient in python:

`
pearsoncorr = dataframe[[ 

    'Temperature - (Celsius)',

    'Nitrous oxide emissions (thousand metric tons of CO2 equivalent)',
    
    'Methane emissions (kt of CO2 equivalent)',
    
    'CO2 emissions (kt)',
    
    'Energy use (kg of oil equivalent per capita)'

]].corr(method='pearson')

`

# Effect Mining
Climate change has different impact on different aspects of society and economics. To achieve this solution, we have have used the following data mining techniques:

# Cluster Analysis
Here we have used important data mining technique called K-means Clustering to find mine important information out of the dataset. Following steps were followed as a pre-processing step to perform effect mining using K-means algorithm:
`
a. Select an indicator

b. Categorize data into 3 decades, 1990-2000, 2000-2010, 2010-2020

c. For each country find mean values of each indicator in those category

d. Calculate percentage change in those values for decades 2000-2010 and 2010-2020 from the 1990-2000

e. Based on percentage change, apply k-means cluster to group data
`

# K-Means Clustering
Here we took important  parameters such as temperature change, rainfall pattern change and different indicators such as land area in agriculture, population growth and others of different countries for different years (decade) and used k-means cluster analysis techniques to group the countries in different clusters. With this we got group of countries based on impact of climate change on those factors. This information can be used by concerned agencies such as world bank and governments of countries that are in those clusters to initiate joint aid efforts, relief or mitigation programs to counter the challenges posed by climate change. Following example shows how we implemented k-means algorithm in python. \newline

`
kmeans = cluster.KMeans(nclusters=3, maxiter = 200000)

kmeans.fit(dataframe[['agri area change 2000', 'agri area change 2010']])

dataframe['cluster label'] = kmeans.labels
`

# Predicting the Future

Climate change has diverse impacts on the socio-economic aspect of the world across different societies.  In this project, we used linear regression to predict the effect of climate change (temperature and rainfall) on different socioeconomic aspects for the coming years (decade of 2020-2030)  so that we can start preparing for the changes to come and also focus on ways of preventing it. Following steps were performed before performing Regression analysis as a pre-processing steps: 

`
a. Extrapolate values of Temperature and Rainfall to find its value for 2020-2030 

b. Based on value of Rainfall, Temperature and Indicators train a Linear Regressor 

c. Predict value of Indicator (eg. cereal yield) using trained model 

d. Use k-means cluster analysis to group similar countries 

`
# Regression Analysis 
Regression analysis is a set of statistical processes for estimating the relationships between a dependent variable and one or more independent variables. In this analysis we model different variable such as cereal production, forest area, GDP contribution of agriculture as dependent variable and temperature, rainfall as independent variable. Using linear regression analysis technique, we then predict the values of those independent variable  from the values of dependent variable. Following code demonstrates implementing linear regressor in Python:

`
regr = linearmodel.LinearRegression()

regr.fit(XTrain, yTrain)

XTest = data[['Temperature - (Celsius)', 'Rainfall - (MM)']]

yPredicted = regr.predict(XTest)
`
