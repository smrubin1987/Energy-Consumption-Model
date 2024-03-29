# Timeseries Analysis and Forecasting: Electricity Consumption Model

## Summary:
Developing a timeseries analysis and forecast for electricity power consumption through an interconnection grid region over multiple years within various associated utility groups in the eastern United States. Data was sourced from Kaggle (https://www.kaggle.com/robikscube/hourly-energy-consumption), from PJM Interconnection LLC - an interstate electricity transmission company.

![](Images/transmissionLines1.jpg)

## Data Wrangling:

[Data Wrangling](https://github.com/smrubin1987/Energy-Consumption-Model/blob/main/DataWrangling_EDA.ipynb)

Data was downloaded as various .csv files, joined using pandas into a pandas DataFrame, and summed based on overlapping years (6-year period) of different utility organizations within the overhead PJM Interconnect company. The data was downloaded as megawatts per hour per utility company, which was then summed per day, then per week. The weekly resampled dataset suggested better stationarity, which was utilized to build and test the models 

![](Figures/plot_weekly.JPG)

## Exploratory Data Analysis:
[EDA](https://github.com/smrubin1987/Energy-Consumption-Model/blob/main/DataWrangling_EDA.ipynb)
Seasonality exists throughout each year, showing increases in power consumption in both winter and summer, with infrequent spikes and troughs of power consumption (likely relating to unforeseen events such as extreme weather occurences). Throughout the 6 year period of analysis, the data appears to maintain stationarity, which is appearent through analysis of the dicky-fuller test. 

## Train - Test Datasets
The first 5 years of the data was used for training the model, and the 6th year of data was utilized for the test set. 

## Augmented Dicky-Fuller Test

[ADF](https://github.com/smrubin1987/Energy-Consumption-Model/blob/main/Dicky-Fuller%20Testing.ipynb)

Augmented Dicky-Fuller Test for stationarity of time series data from sklearn.

![](Figures/adfuller_weekly.JPG)

## Modeling 

[Persistence](https://github.com/smrubin1987/Energy-Consumption-Model/blob/main/PersistenceModel.ipynb)

[ARIMA](https://github.com/smrubin1987/Energy-Consumption-Model/blob/main/ARIMA_Model.ipynb)

[RFR](https://github.com/smrubin1987/Energy-Consumption-Model/blob/main/RandomForestRegression_Model.ipynb)

To forecast the timeseries data, I deployed two machine learning models: i) Persistence Model; ii) Autoregressive Integrated Moving Average (ARIMA) model from sklearn; and ii) Random Forest Regressor model from sklearn. These were compared to a "persistence" model using root mean squarred error (rmse) as a model metric of accuracy. If either model suggested improved accuracy within the forecast, deploying machine learning models may improve the transmission company's capacity for predicting energy consumption throughout the subsequent years over the persistence model. The ARIMA(7,0,2) model showed the lowest RMSE score, suggesting the highest accuracy forecasting model.

![](Figures/ARIMA_7_0_2_Model.jpg)

![](Figures/RMSE_Comparison.jpg)

## Conclusions

[Metrics](https://github.com/smrubin1987/Energy-Consumption-Model/blob/main/RMSE_ModelMetrics.ipynb)

[Slides](https://github.com/smrubin1987/Energy-Consumption-Model/tree/main/SlideDeck)

Using machine learning models to improve the accuracy of timeseries forecasting, in this case for energy consumption, can provide improved accuracy. There are a multitude of hyperparameter tuning, data wranging, and feature engineering possibilities that might improve forecast accuracy. This might include adding holidays, population changes to regions, coorelating the timeseries with weather events, and providing more fine details within the data resolution to train the models. With the basic deployment of machine learning, both ARIMA and RFF improved on the accuracy of the forecast.
