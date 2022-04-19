# Covid Data Analysis with Pyspark ML Pipelines
* [Notebook](https://github.com/youngzyx/covid_predict/blob/main/covid_data_analysis.ipynb)
* [Slides](https://github.com/youngzyx/covid_predict/blob/main/covid_data_analysis.pdf)

## Dataset
Both of the datasets are from the CDC. 
* Dataset1: COVID-19 Case Surveillance Public Use Data with Geography
This patient-level dataset includes demographics and geography features such as sex, ethnicity, exposure history, county and state of residence, death or not, etc. 

* Dataset2: COVID-19 Vaccinations in the United States by County
Dataset 2 is a aggregated data that includes covid-19 vaccine administration and vaccine equity data at county level.

* URLs: 
** Dataset1: https://data.cdc.gov/Case-Surveillance/COVID-19-Case-Surveillance-Public-Use-Data-with-Ge/n8mc-b4w4
** Dataset2: : https://data.cdc.gov/Vaccinations/COVID-19-Vaccinations-in-the-United-States-County/8xkx-amqh

## Data Pre-processing
Build an ETL pipeline for data pre-processing:
* Covid Data: Drop records with unknown status of death
* Vaccination Data: Group data to month level and count number of vaccinated
*Merged two datasets: Merge covid and vaccination data by year-month, state and county.

Execution Time: 0.46s
Cluster : 8 Node i3.xlarge cluster with 9.1 LTS (includes Apache Spark 3.1.2, Scala 2.12)

## Analytical Goals
* Predict the probability of death of patients
* Predict the amount of Covid death with time series model
* Predict the cumulative vaccinated population with time series model

## Implementation
Analytical Goal #1: Predict the probability of death of patients
We used four different models to predict the probability of death of patients:

| Model | Accuracy | Area under ROC | Area under PR | F1 | Execution Time |
| :---- | :-----:  | :-----------:  | :----------:  | :---:  | --------:  |
| Logistic Regression| 0.945 | 0.908 | 0.563 | 0.932 | 12.77 sec |
Decision Tree
0.935
0.526
0.306
0.925
4.63 sec
Random Forest
0.946
0.910
0.573
0.930
15.69 sec
K-means
0.812
 -
-
-
2.59 sec


