---
title      : Titanic Survival Predictions
subtitle   : Coursera Project
author     : Nguyen Thanh Trung
framework  : io2012
highlighter: highlight.js
hitheme    : zenburn
mode: selfcontained
---

## About the product

Using the Titanic survival data available at **Kaggle** (https://www.kaggle.com/c/titanic-gettingStarted/data), 
we were able to build a prediction model was built. Based on your age, ticket class, gender and 
number of family members onboard, we can predict your chance of surviving the Titanic shipwreck.

A Titanic survival dataset contains
- Passenger's name, age, sex
- Ticket type, boarding location
- Whether he survives

---

## Titanic Data


```
## 'data.frame':	891 obs. of  5 variables:
##  $ Survived: int  0 1 1 1 0 0 0 0 1 1 ...
##  $ Pclass  : int  3 1 3 1 3 3 1 3 3 2 ...
##  $ Sex     : Factor w/ 2 levels "female","male": 2 1 1 1 2 2 2 2 1 1 ...
##  $ Age     : num  22 38 26 35 35 NA 54 2 27 14 ...
##  $ Parch   : int  0 0 0 0 0 0 0 1 2 0 ...
```

---

## Building prediction model

Based on the data, a simple prediction model was built.


```r
goodColumnsNoLabel <- c("Pclass", "Sex", "Age", "Parch")
goodColumns <- c("Survived", goodColumnsNoLabel)
Titanic <- Titanic[, goodColumns]
Titanic$Pclass <- factor(Titanic$Pclass)
Titanic$Survived <- factor(Titanic$Survived)
Titanic$Parch <- factor(Titanic$Parch)
modelFit <- train(Survived ~ ., data = Titanic, method = "glm")
```

---

## Final product

The final product was made available online at: https://thanhtnguyen.shinyapps.io/Coursera/

User can select their own scenario and our server will make predictions for them
