# Binary Prediction of Flight Delays – San Jose Airport (SJC)
This project aims to predict whether flights departing from San Jose International Airport (SJC), California are delayed or not, using binary classification models trained on a cleaned subset of the Flight Delay Dataset 2018–2024 from Kaggle.

## Resources
The notebook containing the code was provided within the source files. However, if you wish to see the Google Collab version, you can find it [here](https://colab.research.google.com/drive/18goYM5GGeQgMENW6jTGsoLAh27j9pQDC?usp=sharing). 

## Objective
Predict whether a flight will be delayed by 15 minutes or more (DepDel15 = 1) or not (DepDel15 = 0), using historical flight data.

## Dataset Overview

- Source: [Kaggle Dataset](https://www.kaggle.com/datasets/shubhamsingh42/flight-delay-dataset-2018-2024)
- Scope: Only January 2018 data used.
- Initial shape: ~500,000 instances, 119 features
- Filtered to: San Jose (SJC) departures only
- Final cleaned dataset: 3,880 rows, 67 features
