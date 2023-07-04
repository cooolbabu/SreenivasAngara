---
title: "Non-Linear Regression models"
date: 2023-07-02T18:25:18-05:00
draft: false

weight: 100

cover:
  image: "images/Non-LinearRegress.png"
  Alt: MIT logo

tags: ["python", "jupyter"]
categories: ["ML", "Classification"]
---

Non-linear regression is a powerful technique used in statistics and machine learning to model and analyze complex relationships between variables. Unlike linear regression, which assumes a linear relationship between the independent and dependent variables, non-linear regression algorithms can capture more intricate and non-linear patterns. This makes them particularly useful when dealing with real-world phenomena where linear relationships are insufficient.

Following Non-Linear regression models are covered in the attached Jypter notebook

### Decision Tree Regressor:

- A decision tree regressor is a non-linear regression algorithm that creates a hierarchical structure of binary decisions to predict the target variable. It splits the data based on feature values and predicts the average value of the target variable within each leaf node. Decision trees are easy to interpret but can suffer from overfitting.

### Bagging Regressor:

- The Bagging Regressor is an ensemble learning algorithm that combines multiple decision tree regressors. It trains each decision tree on a random subset of the training data, allowing them to learn different patterns. The final prediction is the average of the predictions made by each tree. Bagging helps reduce overfitting and improves model stability.

### Random Forest Regressor:

- Random Forest is another ensemble algorithm that builds a collection of decision trees. It introduces randomness by selecting a subset of features at each split and training each tree independently. Random Forests are effective in capturing complex non-linear relationships and provide robust predictions by aggregating the outputs of multiple trees.

### Ada Boost Regressor:

- Ada Boost (Adaptive Boosting) is an ensemble algorithm that combines weak learners into a strong learner. In the context of regression, weak learners are decision trees with limited depth. Ada Boost assigns higher weights to data points that were incorrectly predicted by previous models, allowing subsequent models to focus on those points. It iteratively improves predictions by adjusting the weights of the weak learners.

### Gradient Boosting Regressor:

Gradient Boosting Regressor is another ensemble algorithm that combines weak learners, typically decision trees, in a sequential manner. It fits each subsequent tree to the residual errors of the previous tree. By minimizing the errors in a gradient descent-like manner, Gradient Boosting produces a strong predictive model. It is particularly effective in handling complex non-linear relationships.

### XG Boost Regressor:

- XG Boost (Extreme Gradient Boosting) is an optimized implementation of the Gradient Boosting algorithm. It uses a more efficient and accurate tree-building process, handling missing values, regularization techniques, and parallel processing. XG Boost has gained popularity due to its high performance and effectiveness in various regression problems.

These regression models offer different trade-offs in terms of interpretability, accuracy, and computational complexity. Choosing the most suitable model depends on the specific problem and dataset characteristics. It is often beneficial to experiment and compare multiple models to find the best fit for the task at hand.

### Performance Report

![Non-Linear Regression PR](Non-LinearRegressPR.png)

The highlighted model is a tuned Random Forest Regressor using GridSearch. We can see that both R-Squre and Adjusted R-Square are higher and error scores are lower than models that are not tuned. Tuning the hyperparameters of a machine learning model can help improve its performance.

### Feature Importance

We can extract important features and visualize them. Here

- The most important features are Department_gynecology, Age_41_50, and Age_31_40, followed by Department_anesthesia, Department_radiotherapy, and Admission_Deposit.
- The rest of the variables have little or no influence on the length of stay in the hospital in this model.

![Feature Importance](feature_importance.png)

🔗 [Jupyter Notebook](https://github.com/cooolbabu/GL-MIT-ADSP-2023/blob/master/capstone/Hospital_LOS_Prediction.ipynb) 🔗 [HTML version ](https://cooolbabu.github.io/ConversationsWithChatGPT/Hospital_LOS_Prediction.html)
