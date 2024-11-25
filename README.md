# Time Series Forecasting for Metro Train Compressor Predictive Maintenance

This repository contains a time series analysis project aimed at building predictive models for the maintenance of metro train compressors. The dataset consists of sensor readings from the Air Production Unit (APU) of the compressors recorded from February to August 2020. The project leverages various time series forecasting techniques to predict potential anomalies and optimize the maintenance schedule for the metro system.

## Table of Contents
1. [Introduction](#introduction)
2. [Data Description](#data-description)
3. [Objective](#objective)
4. [Data Cleaning](#data-cleaning)
5. [Data Decomposition](#data-decomposition)
6. [Smoothing Methods](#smoothing-methods)
7. [Testing Stationarity](#testing-stationarity)
8. [Justification for Time Series](#justification-for-time-series)
9. [Implementation and Forecasting](#implementation-and-forecasting)
10. [Model Selection](#model-selection)
11. [Comparative Result Analysis](#comparative-result-analysis)
12. [Google Colab Link](#google-colab-link)
13. [Conclusion](#conclusion)
14. [Future Scope](#future-scope)
15. [References](#references)

## Introduction

Given the growing need to enhance operational reliability and predictive maintenance in metro systems, this project focuses on the sensor data of metro train compressors. Key parameters such as temperature, pressure, motor current, and oil temperature influence the performance of the Air Production Unit (APU), which is crucial for the functioning of the metro system. The primary goal of this project is to apply time series analysis to predict anomalies and improve maintenance strategies.

This project takes you through the entire pipeline—from data cleaning and decomposition to forecasting and result evaluation. Different time series models are employed, including ARIMA, Auto-ARIMA, VAR, Prophet, and LSTM, to provide an accurate prediction of system behavior and help in proactive maintenance.

## Data Description

The dataset consists of minute-wise sensor readings from February to August 2020. It includes the following key features:

- **Timestamp**: Date and time of data collection.
- **TP2, TP3, H1**: Sensor values indicating pressure and temperature in different system components.
- **DV_pressure**: Pressure readings related to system performance.
- **Reservoirs**: Status of the reservoir systems.
- **Oil_temperature**: The oil temperature, a vital parameter for mechanical health.
- **Motor_current**: Electrical current readings, which help assess the energy consumption of the compressor.
- **Status**: Operational status of the system (e.g., functioning or malfunctioning).

These features make the dataset ideal for time series analysis, which will be used to identify trends, seasonality, and anomalies over time.

## Objective

The main objectives of this project are:

1. **To Analyze Historical Sensor Data**: Identify trends, seasonality, and anomalies in the sensor readings.
2. **To Build Accurate Predictive Models**: Develop time series models to forecast future sensor values.
3. **To Enable Proactive Maintenance**: Use the forecasts to schedule maintenance before system failures occur.
4. **To Enhance Operational Efficiency**: Minimize repair costs by shifting towards predictive maintenance strategies.

## Data Cleaning

Before applying time series models, the dataset underwent extensive cleaning:

1. **Data Reduction**: Due to the large dataset size, the timestamps were reduced from second-wise to minute-wise intervals.
2. **Column Transformation**: Binary columns were converted to integer values for ease of analysis.
3. **Datetime Conversion**: Ensured that the timestamp column was correctly formatted as a datetime object to facilitate time series operations.
4. **Data Filtering**: Filtered the dataset to include only data from April to July 2020, as the full dataset was too large for initial analysis.

## Data Decomposition

Time series data typically comprises three components:

1. **Trend**: The overall movement or direction in the data.
2. **Seasonality**: Repeating patterns or cycles in the data.
3. **Residual**: The remaining noise or unexplained variation in the data.

In this case, the dataset did not exhibit any clear seasonality, as observed through decomposition plots.

## Smoothing Methods

To improve the accuracy of forecasting models and reduce the impact of irregularities in the data, several smoothing techniques were applied:

1. **Simple Exponential Smoothing (SEE)**
2. **Double Exponential Smoothing (DEE)**
3. **Triple Exponential Smoothing (TEE)**

Each method progressively accounted for trend and seasonality, allowing us to better capture patterns in the data.

## Testing Stationarity

Stationarity is a crucial requirement for many time series models. We applied the **Augmented Dickey-Fuller (ADF) test** to check for stationarity in the data. Initially, the dataset showed non-stationary behavior due to identifiable trends and seasonality. We applied differencing techniques to transform the data into a stationary form suitable for ARIMA modeling.

## Justification for Time Series

This dataset is classified as a time series due to the following reasons:

- **Sequential Dependency**: The sensor readings depend on past values, indicating temporal relationships.
- **Trend and Seasonality**: The presence of these patterns over time requires time series models to capture their dynamics.
- **Forecasting Objective**: The need to predict future values based on historical data is the core of time series analysis.

## Implementation and Forecasting

The following models were implemented to forecast future sensor values:

1. **ARIMA (AutoRegressive Integrated Moving Average)**: A widely-used model for time series forecasting, which requires the data to be stationary. ARIMA models the data as a combination of past values (AR), past forecast errors (MA), and differenced data (I).
2. **Auto-ARIMA**: An automated approach to identify the best ARIMA parameters (p, d, q) using model selection criteria like AIC and BIC.
3. **VAR (Vector AutoRegression)**: Used for multivariate time series data, where multiple variables influence each other over time.
4. **Prophet**: A powerful model developed by Facebook, designed to handle time series with strong seasonal patterns and irregular trends.
5. **LSTM (Long Short-Term Memory)**: A type of Recurrent Neural Network (RNN) ideal for capturing non-linear and long-term dependencies in the data.

## Model Selection

Each model was selected based on the nature of the data and the specific characteristics of the features:

- **LSTM** was chosen for capturing complex, non-linear relationships in the data.
- **Auto-ARIMA** was used for features exhibiting clear trends and seasonality.
- **Prophet** was chosen for its ability to handle strong seasonal components and irregular patterns.
- **VAR** was applied to capture relationships between multiple variables.

## Comparative Result Analysis

We compared the performance of the models using several error metrics:

- **Mean Error (ME)**
- **Root Mean Squared Error (RMSE)**
- **Mean Absolute Error (MAE)**
- **Mean Absolute Percentage Error (MAPE)**

These metrics allowed us to assess the accuracy and reliability of each forecasting method.

## Google Colab Link

The complete implementation of the project is available on [Google Colab](<insert_link_here>), where you can interact with the code and run the analyses yourself.

## Conclusion

In this project, different time series models were explored to forecast the sensor readings for metro train compressors. Each model had its strengths and limitations, with LSTM emerging as the most versatile model for this dataset. The choice of models was guided by the nature of the data and the goal of achieving accurate forecasts for predictive maintenance.

## Future Scope

- **Model Improvement**: Experimenting with more complex models like Transformer Networks or combining multiple models (e.g., ensemble methods).
- **Real-time Deployment**: Implementing the model in a real-time system for continuous monitoring and anomaly detection.
- **Expanded Data**: Including more features and data from other parts of the metro system to improve model accuracy.

## References

- [ARIMA Documentation](https://statsmodels.github.io/statsmodels/)
- [Prophet Documentation](https://facebook.github.io/prophet/docs/)
- [LSTM Explained](https://colah.github.io/posts/2015-08-Understanding-LSTMs/)
