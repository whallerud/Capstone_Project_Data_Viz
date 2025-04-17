# Titanic: Who Was Left Behind?  
### A Machine Learning Narrative About Loss, Survival, and Mystery

---

## Objective

Rather than asking *who survived the Titanic disaster*, this project flips the question to ask:

> **Who was left behind?**

We explored this inverted classification challenge to shift our perspective on the classic Titanic dataset and reframe the goal of survival prediction models.

---

## Summary

Using the Kaggle Titanic dataset, we trained three machine learning models — **Logistic Regression**, **K-Nearest Neighbors**, and **Decision Tree Classifier** — to predict **non-survivors** based on passenger characteristics. We engineered new features (`Title`, `FamilySize`), handled missing data, and standardized inputs for consistency.

We also added a twist by identifying **"mystery survivors"** — passengers our models confidently predicted would not survive, but did anyway. These cases helped surface patterns of social advantage and anomaly in historical outcomes.

---
git 
## Data Preprocessing

- Dropped: `Name`, `Ticket`, `Cabin`, `PassengerId`
- Filled Missing:
  - `Age` → Median
  - `Fare` → Median (for test set)
  - `Embarked` → Mode
- Encoded: `Sex`, `Embarked`, `Title`
- Engineered:
  - `Title` extracted from name
  - `FamilySize` = SibSp + Parch + 1
- Normalized: `Age`, `Fare`, `FamilySize`

---

## Models Tested

| Model               | Key Params        | Accuracy |
|--------------------|-------------------|----------|
| Logistic Regression | max_iter=1000     | ~80%     |
| K-Nearest Neighbors | n_neighbors=3     | ~81%     |
| Decision Tree       | max_depth=5       | ~80%     |

All models were evaluated on test data using accuracy and classification reports. A comparison CSV and bar plot are included in the notebook.

---

## "Mystery Survivors" Feature

We searched for high-confidence model misclassifications — passengers predicted *not to survive* but who actually did. These became the emotional and narrative core of our exploration.

This approach helped us explore:

- Gender bias in survival
- Social class and rescue priority
- Model limitations on rare but important edge cases

---

## SQL Storage (Optional Step)

The cleaned dataset and model results were written to a PostgreSQL database via SQLAlchemy for persistent storage and potential integration with BI tools.

---

## Visualization

- Model comparison bar plot
- Optional: highlight “mystery survivors” by feature (age, class, sex)
- Tools used: `matplotlib`, `pandas`

---

## Files in This Repository
