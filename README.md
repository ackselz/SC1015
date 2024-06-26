# Hotel Booking Cancellation Prediction

[Presentation Video](https://www.youtube.com/watch?v=UICKs8zISyc)

## Overview

This is a Mini-Project for SC1015 (Introduction to Data Science and Artificial Intelligence). This project aims to investigate the likelihood of a hotel booking cancellation using a dataset of hotel bookings. The project involves exploratory data analysis (EDA), data preprocessing, and the training of various machine learning models to predict booking cancellations. The models employed include logistic regression, K-nearest neighbors (KNN), AutoML, and neural networks.

## Data

The dataset used in this project contains information about hotel bookings, including details such as reservation status (cancelled or not cancelled), lead time, arrival date, number of nights booked, number of people, meal plan, country of origin, and other relevant features. The dataset is obtained from [the source](https://www.kaggle.com/datasets/ahsan81/hotel-reservations-classification-dataset).

## Contributors

- @ackselz: K-Nearest Neighbours, AutoML, Random Forest, Neural Network
- @Pavperera: Data Extraction, Data Visualization, Data Resampling, Logistic Regression

## Problem Definition

- How do different variables affect the probability of a hotel booking being cancelled?
- Are we able to predict which hotel bookings will likely be cancelled?

## Exploratory Data Analysis

Univariate, Bivariate, and Multivariate Visualization and analysis were used to determine the relationships between each variable and a booking being cancelled. 
- `lead_time`: the duration in advance a booking is made showed to have the highest correlation with a booking being cancelled. The earlier a booking is made, the more likely it is cancelled. This could be due to customers having higher chances of a change in travel plans or more time to source for better deals.
- `avg_price_per_room`: the average price of the room booking showed to have a correlation with a booking being cancelled. The higher the price of a booking, the more likely it is cancelled. This could be due to customers finding better deals and cancelling their bookings, assuming there are free cancellations.

## Data Balancing/Resampling

It was observed that the original dataset was slightly imbalanced in the target `booking_status` column, with only 32.8% of samples being `Canceled` and the remaining 67.2% being `Not_canceled`. This could potentially lead to bias towards the majority class (`Not_cancelled`) and mislead our evaluation metrics. Hence, we explored the use of data balancing techniques to balance the datasets, and subsequently trained the same models and evaluated the performance of these new models. 

Data balancing techniques used:
- Random Oversampling -> [`predictive-modelling-random-oversampled.ipynb`](predictive-modelling-random-oversampled.ipynb)
- Synthetic Minority Oversampling Technique (SMOTE) -> [`predictive-modelling-SMOTE.ipynb`](predictive-modelling-SMOTE.ipynb)

However, the discussions are done in relation to the original dataset, as we deemed that data resampling did not result in a significant difference in observations.

## Models Used

- Logistic Regression
  - Simple baseline model
  - Easily implemented
  - Highly interpretable

- K-Nearest Neighbours (KNN)
  - Better capture non-linear relationships and complex feature relationships
  - To increase robustness to outliers
  - Non-parametric

- AutoML ([tpot](https://epistasislab.github.io/tpot/)) -> **Random Forest**
  - To explore the use of Automated Machine Learning
  - Efficient and effective way to find the best models for a specific classification task

- Neural Network
  - To explore how a simple neural network would perform compared to the more common algorithms above

### Original Dataset

The discussions can be found in [`predictive-modelling.ipynb`](predictive-modelling.ipynb). The discussions are done in relation to the original dataset, as we deemed that data resampling did not result in a significant difference in observations.

*(descending Precision)*

| Modal | Accuracy Score | F1 score | Precision | Recall |
|-------|-----------------|----------|-----------|--------|
|Random Forest|0.900430|0.927673|0.908535|0.947635|
|Neural Network|0.782115|0.833558|0.858879|0.809687|
|K-Nearest Neighbors|0.806814|0.861699|0.832393|0.893144|
|Logistic Regression|0.806925|0.862526|0.829007|0.898871|

### Dataset with Random Oversampling

*(descending Precision)*

| Model | Accuracy Score | F1 score | Precision | Recall |
|-------|-----------------|----------|-----------|--------|
|Random Forest|0.920541|0.922856|0.901820|0.944897|
|Logistic Regression|0.817958|0.821342|0.811030|0.831920|
|K-Nearest Neighbors|0.791226|0.802605|0.765228|0.843821|
|Neural Network|0.784420|0.814611|0.717783|0.941637|

### Dataset with SMOTE

*(descending Precision)*

| Model | Accuracy Score | F1 score | Precision | Recall |
|-------|-----------------|----------|-----------|--------|
|Random Forest|0.919065|0.921461|0.900047|0.943919|
|Logistic Regression|0.821976|0.825496|0.814175|0.837137|
|Neural Network|0.822140|0.839393|0.768959|0.924030|
|K-Nearest Neighbors|0.791226|0.802605|0.765228|0.843821|

## Conclusion

**Yes, we are able to predict which hotel bookings will be cancelled with a high degree of accuracy and precision.**
- Lead Time has a moderate positive correlation with cancellation rate. A longer lead time increases likelihood of booking being cancelled.
- Bookings made with a higher price also has a slightly higher likelihood of being cancelled.
- A tuned random forest model is the best at predicting which hotel bookings will be cancelled (Accuracy = 0.9, Precision = 0.91).

**Hotels can consider implementing some strategies to reduce/react to cancellations.**
- Implement higher cancellation fees for bookings made earlier in advance. Especially, if price of booking was higher than on average.
- Use the Random Forest Model to predict which bookings will be cancelled with 90% precision and account for cancellations by overbooking rooms (to ensure 100% occupancy).

## Takeaways

- Oversampling of data does not necessarily improve model results, despite original dataset having a high imbalance.
  - Other resampling methods can be explored in the future to determine if data resampling could improve the model performance
- AutoML performs extremely well to identify the model that performs the best.
  - By leveraging AutoML, the Random Forest model was able to find the optimal combination of hyperparameters, such as the number of trees, maximum depth, and feature selection criteria, which maximized its predictive       accuracy for the hotel booking cancellation prediction task. This automated tuning process likely led to a more robust and well-performing model compared to other models that were not optimized through AutoML or were tuned manually.

