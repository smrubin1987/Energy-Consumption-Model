# Timeseries Analysis and Forecasting: Electricity Consumption Model
![alt text](https://github.com/smrubin1987/Energy-Consumption-Model/tree/main/Images/transmissionLines.jpg?raw=true)
## Summary:
Developing a timeseries analysis and forecast for electricity power consumption through an interconnection grid region over multiple years within various associated utility groups in the eastern United States. Data was sourced from Kaggle (https://www.kaggle.com/robikscube/hourly-energy-consumption), from PJM Interconnection LLC - an interstate electricity transmission company.

## Data Wrangling:
Data was downloaded as various .csv files, joined using pandas into a pandas DataFrame, and summed based on overlapping years (6-year period) of different utility organizations within the overhead PJM Interconnect company. The data was downloaded as megawatts per hour per utility company, which was then summed per day, then per week. 

## Exploratory Data Analysis
Seasonality exists throughout each year, showing increases in power consumption in both winter and summer, with infrequent spikes and troughs of power consumption (likely relating to unforeseen events such as extreme weather occurences). Throughout the 6 year period of analysis, the data appears to maintain stationarity, which is appearent through analysis of the dicky-fuller test. 

## Train - Test Datasets
The first 5 years of the data was used for training the model, and the 6th year of data was utilized for the test set. 

## Modeling 
To forecast the timeseries data, I deployed two machine learning models: i) Autoregressive Integrated Moving Average (ARIMA) model from sklearn; and ii) Random Forest Regressor model from sklearn. These were compared to a "persistence" model using root mean squarred error (rmse) as a model metric of accuracy. If either model suggested improved accuracy within the forecast, deploying machine learning models may improve the transmission company's capacity for predicting energy consumption throughout the subsequent years over the persistence model.

## Conclusions
Using machine learning models to improve the accuracy of timeseries forecasting, in this case for energy consumption, can provide improved accuracy. There are a multitude of hyperparameter tuning, data wranging, and feature engineering possibilities that might improve forecast accuracy. This might include adding holidays, population changes to regions, coorelating the timeseries with weather events, and providing more fine details within the data resolution to train the models. With the basic deployment of machine learning, both ARIMA and RFF improved on the accuracy of the forecast.
