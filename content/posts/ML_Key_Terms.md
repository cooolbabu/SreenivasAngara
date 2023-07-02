---
title: "Machine Learning - Key terms"
date: 2023-06-17T18:25:18-05:00
draft: false

weight: 500

cover:
  image: "images/questions2.png"
  Alt: MIT logo
  imageWidth: 200
  imageHeight: 200

tags: ["python", "jupyter"]
categories: ["ML", "ML_Terms"]
---

During an interview process, interviewers generally ask and expect textbook definitions of basic terms. Interviewees, on the other hand must be prepared and answer them promptly. Lengthy and exploratory answers prevent interviewers from asking more probing questions.

I noticed this issue on a recent interview and not repeat this mistake.

#### Confidence Interval

A confidence interval is a range of values around the point estimate, constructed so that this range will contain the population parameter with a certain degree of confidence, expressed in percentage terms. Used for testing null hypothesis

#### Variance

To calculate the variance, we take the difference between each number in the dataset and the mean of the data, square this difference to make it positive (independent of sign), and finally divide the sum of the squares by the total number of values in the dataset.

#### Bias

Bias is the amount by which a model’s predictions differ from the target values, on the training data, i.e., the training error

#### Bias-Variance Trade-off

If we increase the bias of an overfit model, we are making the model simpler and capable of generalizing over the validation set. Its performance on the validation set will improve and, consequently, the variance will decrease. On the other hand, if we decrease the bias of an underfit model, we are making the model more complex and the model will fit the training data more closely and, consequently, the variance will increase. This phenomenon is called the **Bias-Variance tradeoff.**

**Homoscedasticity -** If the residuals are symmetrically distributed across the regression line, then the data is said to be homoscedastic.

**Heteroscedasticity -** If the residuals are not symmetrically distributed across the regression line, then the data is said to be heteroscedastic. In this case, the residuals can form a funnel shape or any other non-symmetrical shape

**Q_Q plot:** The plot obtained is known as a quantile-quantile plot, or Q_Q plot, when the quantiles of two variables are placed against one another. With respect to the locations, this plot summarises whether or not the distributions of two variables are similar.

**Pearsonr:** A linear relationship between two variables' strength and direction is measured by the Pearson correlation coefficient. Values usually fall between -1 and 1, with 1 denoting a perfectly positive correlation and -1 denoting a perfectly inverse relationship.

#### Linear Regression Model performance

- **R-squared:** R-squared is a useful performance metric to understand how well the regression model has fitted over the training data. For example, an R-squared of 80% reveals that the model is able to capture 80% of the variation in the dependent variable. A higher R-squared value indicates a better fit for the model.
- **Adjusted R-squared:** The adjusted R-squared is a modified version of R-squared that takes into account the number of independent variables present in the model. The R-squared always increases when a new independent variable is added to the model, irrespective of whether that variable adds value to the model or not. Hence, R-squared might be misleading when we have multiple independent variables and cannot identify unnecessary variables included in the model.
- **RMSE:** RMSE stands for Root Mean Squared Error. It is calculated as the square root of the mean of the squared differences between the actual output and the predictions. The lower the RMSE the better the performance of the model. Mathematically, it can be given as follows:
  - However, when a new variable is added, the adjusted R-squared increases if that variable adds value to the model, and decreases if it does not. Hence, adjusted R-squared is a better choice of metric than R-squared to evaluate the quality of a regression model with multiple independent variables, because adjusted R-squared only remains high when all those independent variables are required to predict the value of the dependent variable well; it decreases if there are any independent variables which don't have a significant effect on the predicted variable.

#### Classification model performance

- Accuracy - Overall Accuracy of the model.
- Precision - Use Precision to minimize False Negatives - Ideal for maketing campaigns
- Recall - Use Recall to minimize False Positives - Telling someone he/she has 'Cancer' when not true
- F1-Score - Geometric mean of Precision and Recall. Overall Model performance
- Area under curve - Coverage of accurate predictions.
