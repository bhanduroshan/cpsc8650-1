# Introduction
In the recent decade, we have seen world being more and more industrialized. With industrialization, countries appear to produce more and more greenhouse gases. Global temperature is rising and rainfall id getting erratic, this is causing problems in different sectors of our society and the world. In this project we mine the climate change data set from the World Bank and analyze the cause, the effect and predict the future so that we can initiate mitigation steps for the problems caused by climate change. 

# Cause Mining
## Correlation Analysis 
Following code demonstrates how we implemented correlation analysis using Pearson's coefficient in python:

```
pearsoncorr = dataframe[[ 
    'Temperature - (Celsius)',
    'Nitrous oxide emissions (thousand metric tons of CO2 equivalent)',
    'Methane emissions (kt of CO2 equivalent)',
    'CO2 emissions (kt)',
    'Energy use (kg of oil equivalent per capita)'
]].corr(method='pearson')

```

# Effect Mining
## Cluster Analysis 
Following steps were followed as a pre-processing step to perform effect mining using K-means algorithm:

```
a. Select an indicator
b. Categorize data into 3 decades, 1990-2000, 2000-2010, 2010-2020
c. For each country find mean values of each indicator in those category
d. Calculate percentage change in those values for decades 2000-2010 and 2010-2020 from the 1990-2000
e. Based on percentage change, apply k-means cluster to group data
```

### K-Means Clustering
Following example shows how we implemented k-means algorithm in python.

```
kmeans = cluster.KMeans(nclusters=3, maxiter = 200000)
kmeans.fit(dataframe[['agri area change 2000', 'agri area change 2010']])
dataframe['cluster label'] = kmeans.labels
```

# Predicting the Future
Following steps were performed before performing Regression analysis as a pre-processing steps: 

```
a. Extrapolate values of Temperature and Rainfall to find its value for 2020-2030 
b. Based on value of Rainfall, Temperature and Indicators train a Linear Regressor 
c. Predict value of Indicator (eg. cereal yield) using trained model 
d. Use k-means cluster analysis to group similar countries 
```

## Regression Analysis 
Using linear regression analysis technique, we then predict the values of those independent variable  from the values of dependent variable. Following code demonstrates implementing linear regressor in Python:

```
regr = linearmodel.LinearRegression()
regr.fit(XTrain, yTrain)
XTest = data[['Temperature - (Celsius)', 'Rainfall - (MM)']]
yPredicted = regr.predict(XTest)
```

# Steps on Running the code

```
a. Download the repository or git clone the repository
b. Open Jupyter notebook
c. Open the main.py.ipynb file

```

Alternatively to view the code and results, you can also click: https://github.com/ym96/cpsc8650/blob/master/main.py.ipynb
