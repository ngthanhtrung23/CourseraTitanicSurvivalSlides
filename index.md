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
## Error: could not find function "getURL"
```

```
## Error: incorrect number of dimensions
```

```
##  table [1:4, 1:2, 1:2, 1:2] 0 0 35 0 0 0 17 0 118 154 ...
##  - attr(*, "dimnames")=List of 4
##   ..$ Class   : chr [1:4] "1st" "2nd" "3rd" "Crew"
##   ..$ Sex     : chr [1:2] "Male" "Female"
##   ..$ Age     : chr [1:2] "Child" "Adult"
##   ..$ Survived: chr [1:2] "No" "Yes"
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

User can select their own scenario, including:
1. Age
2. Gender
3. Ticket type
4. Number of family members onboard

and our server will make predictions for them. The result will then 
be displayed in a user friendly manner to the user.
