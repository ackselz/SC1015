# Hotel Booking Cancellation Prediction

## Overview
This is a Mini-Project for SC1015 (Introduction to Data Science and Artificial Intelligence). This project aims to investigate the likelihood of a hotel booking cancellation using a dataset of hotel bookings. The project involves exploratory data analysis (EDA), data preprocessing, and the training of various machine learning models to predict booking cancellations. The models employed include logistic regression, K-nearest neighbors (KNN), AutoML, and neural networks.

## Data
The dataset used in this project contains information about hotel bookings, including details such as reservation status (cancelled or not cancelled), lead time, arrival date, number of nights booked, number of people, meal plan, country of origin, and other relevant features. The dataset is not included in this repository due to privacy concerns, but it can be obtained from [Source](https://www.kaggle.com/datasets/ahsan81/hotel-reservations-classification-dataset).

## Contributors
- @ackselz: Logistic Regression, KNN, AutoML, Neural Network
- @Pavperera: Data Visualization, Data Extraction

## Problem Definition
How do different variables affect the probability of a hotel booking being cancelled?
Are we able to predict which hotel bookings will likely be cancelled?

## Exploratory Data Analysis
Univariate, Bivariate, and Multivariate Visualization and analysis were used to determine the relationships between each variable and a booking being cancelled. 
- `lead_time`: the duration in advance a booking is made showed to have the highest correlation with a booking being cancelled. The earlier a booking is made, the more likely it is cancelled. This could be due to customers having higher chances of a change in travel plans or more time to source for better deals.
- `avg_price_per_room`: the average price of the room booking showed to have a correlation with a booking being cancelled. The higher the price of a booking, the more likely it is cancelled. This could be due to customers finding better deals and cancelling their bookings, assuming there are free cancellations.

## Models Used
- Logistic Regression
- K Nearest Neighbours (KNN)
- Neural Network
(add more on the results)

## Conclusion
(To insert)
