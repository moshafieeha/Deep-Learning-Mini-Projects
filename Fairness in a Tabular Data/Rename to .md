## Problem Statement

The goal of this project is to explore fairness in machine learning models. Specifically, we address how different demographic groups (men and women) are treated by the model in terms of prediction probabilities. We aim to identify any biases in the model's predictions and take steps to mitigate these biases to ensure fair treatment across different groups.

## Solution Overview

This project involves building a logistic regression model to predict income levels based on various features. We then evaluate the model's performance and fairness using specific metrics. The main steps include:

1. **Data Preprocessing**: Load and prepare the dataset by encoding categorical variables and splitting it into training and test sets.
2. **Model Training**: Train a logistic regression model on the training data.
3. **Fairness Evaluation**: Calculate fairness metrics such as Zemel Fairness and Disparate Impact to assess the model's bias towards different gender groups.
4. **Fairness Improvement**: Implement methods to improve model fairness, including:
   - **Swapping Data**: Adjust the training data by swapping specific rows to balance the probabilities for different groups.
   - **Model Calibration**: Apply calibration techniques to improve the model's probability estimates.

By addressing these steps, we aim to build a more equitable machine learning model that treats all demographic groups fairly.
