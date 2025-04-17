# Titanic Predictions — Data Science Capstone

This project models survival outcomes on the Titanic using cleaned and engineered features. Multiple classification models are trained and evaluated, with results exported for database and dashboard use.

---

## Project Structure

- `Titanic_Predictions.ipynb` – Core notebook for data exploration, modeling, and exports  
- `Exports/` – Folder containing output CSVs:
  - `titanic_cleaned.csv`
  - `model_results.csv`
  - `beneficiary_survivors.csv`
- `README.md` – Project overview and narrative

---

## Environment Setup (Conda)

To set up your environment using Anaconda:

```bash
conda create -n titanic_env python=3.9
conda activate titanic_env

# Required libraries
conda install pandas scikit-learn seaborn matplotlib sqlalchemy

# Optional: PostgreSQL export support ******************************UNFINISHED
conda install -c conda-forge pg8000
```

---

## Running the Project

Open `Titanic_Predictions.ipynb` in Jupyter Notebook or JupyterLab.

Run all cells in order:

- Cleans and prepares the data
- Trains and evaluates models
- Identifies "unexpected survivors"
- Exports results to CSV and optionally PostgreSQL

---

## CSV Outputs

These files are generated in the `Exports/` folder:

| File Name                  | Description                                      |
|---------------------------|--------------------------------------------------|
| `titanic_cleaned.csv`     | Cleaned dataset with engineered features         |
| `model_results.csv`       | Accuracy results for each model                  |
| `beneficiary_survivors.csv` | Passengers who survived against prediction     |

---

## PostgreSQL Integration

To export the datasets into PostgreSQL, use the built-in function inside the notebook:

```python
export_to_postgresql(engine)
```

This will write the following tables to your PostgreSQL database:

| Table Name             | Source DataFrame     |
|------------------------|----------------------|
| `titanic_cleaned`      | `df_cleaned`         |
| `model_results`        | `results_df`         |
| `beneficiary_survivors`| `beneficiaries_df`   |

Ensure your SQLAlchemy engine is properly configured.

---

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
| Logistic Regression | max_iter=1000     | ~78%     |
| K-Nearest Neighbors | n_neighbors=3     | ~76%     |
| Decision Tree       | max_depth=5       | ~79%     |

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

## Dataset Source

[Kaggle: Titanic - Machine Learning from Disaster](https://www.kaggle.com/c/titanic)

---

##Recieved Assistance From
- Chat Gpt 
-Co Pilot
