---
title: "MIT-GreatLearning Applied Data Science program Capstone Project"
date: 2023-06-17T18:25:18-05:00
draft: false

weight: 100

cover:
  image: "images/mit-logo-1024x293.png"
  Alt: MIT logo
  imageWidth: 200
  imageHeight: 200

tags: ["python", "jupyter"]
categories: ["ML", "Classification"]
---

During my participation in the MIT-GreatLearning Applied Data Science Program, I experienced an intensive curriculum that encompassed diverse subjects such as Statistics, Python programming, Machine Learning, Neural Networks, and Recommendation Systems.

The culmination of the program was the Capstone project, which aimed to predict Loan Default. This involved crucial steps like Data Preparation, Exploratory Data Analysis, constructing models, and generating a comprehensive performance report for the various models employed.

The final outcome is a binary classification.

- True being - the Loan will default
- False - the loan will not default

An essential aspect of being a successful Data Scientist lies in effectively presenting findings. Seaborn, a remarkable visualization tool, played a pivotal role in crafting captivating presentations.

**The following three charts encapsulate the efforts made during the Capstone project.**

### Presentation.1 - Performance of various ML models for Loan default classification

The following table shows the preformance score for each model. F1 Score is measure of models accuracy

![](cap-model-performance.png)

### Presentation.2 - Selecting Top three classification Models for predicting loan default

Every model has a Train and Test score. We would like to see these scores as close as possible.
{{< figure src="cap-perf-report20230618_2.png" alt="Performance Report" width="90%">}}

### Presentation.3 - Selecting the best classification model for loan default

Here both Stacking Classification and HistGradientBoosting Classifier have simillar or closer F1 Scores. Digging deeper
we can see that HistGradientBoosting is better at predicting actual defaults. And that's the winner

!["Confusion Matrix"](Capstone-ConfusionMatrix.png)

🔗 [Jupyter Notebook](https://github.com/cooolbabu/GL-MIT-ADSP-2023/blob/master/capstone/CapstoneProjectLoanDefault_LowCode_SreenivasAngaraM3.ipynb) 🔗 [HTML version ](https://cooolbabu.github.io/ConversationsWithChatGPT/CapstoneProjectLoanDefault_LowCode_SreenivasAngaraFinal3.html)
