# Titanic Anomaly Detection: Mystery Survivors

## Overview

This project re-examines the Titanic dataset from the well-known Kaggle competition:  
**[Titanic - Machine Learning from Disaster](https://www.kaggle.com/competitions/titanic/data)**

Rather than predicting survival in general, we aimed to identify *anomalous survivors*—passengers whom the model predicted would perish, yet survived. These individuals are framed as "suspects" for deeper analysis. 

We anonymized these cases and modeled their profiles to highlight patterns that traditional survival prediction efforts may overlook.

## Methodology

- **Data Ingestion & Cleaning**: Data was retrieved from a cleaned `.csv` exported to SQLite, then loaded into a DataFrame.
- **Preprocessing**: Included normalization, encoding, and standardization of features.
- **Modeling**: 
  - A neural network was trained using TensorFlow/Keras.
  - Initial accuracy exceeded the 75% threshold.
  - An iterative optimization process was conducted to enhance performance.
- **Anomaly Detection**: Final model outputs were compared to actual survival data to isolate “mystery survivors.”

## Results

- The neural network achieved classification accuracy above 75%.
- Anomalous cases (predicted to die, but survived) were extracted and visualized.
- These survivors were analyzed for demographic and class-based patterns.

## Optimization

A sequence of model refinements was recorded, with changes in accuracy, loss, and configuration captured in code and outputs.  
Final model results are clearly displayed within the notebook.

## How to Run

1. Ensure all required packages are installed: `pandas`, `tensorflow`, `matplotlib`, `sqlalchemy`, etc.
2. Load the `.ipynb` file and run sequentially.
3. Outputs and key graphs will appear inline.

## Authors

- Wade Hallerud  
- Chris Thomas  
- Jamie Stark  
- Erik Fraas  
- Assisted by ChatGPT
---

##Recieved Assistance From
- Chat Gpt 
-Co Pilot
