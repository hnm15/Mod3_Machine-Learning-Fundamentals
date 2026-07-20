## NEED 2 EDIT 

# Module 3: Machine Learning Fundamentals

This repository contains coursework and projects completed for the Machine Learning Fundamentals course, part of my Master's in Data Science at Boston University. Specifically, it includes individual homework assignments and a group project predicting home tax-assessed value based a collection of 55 features and using 77,613 entries of the Zillow housing dataset.

**Highlight:** The group project's final tuned model (Bagging Regressor) improved RMSE from a $462,458.49 baseline (untuned Decision Tree) down to ~$414K–$437K through feature engineering, feature selection, and hyperparameter tuning guided by validation curves. → [Full writeup and results](./Group_Project_Zillow_Housing_Dataset/README.md)


This work demonstrates practical experience with:
- Data exploration and visualization
- Data cleaning and preprocessing
- Feature engineering and feature selection
- Regression modeling (linear, polynomial, tree-based, ensemble)
- Model evaluation and hyperparameter tuning
- Communicating machine learning results to technical and non-technical audiences

## Repository Structure

```
├── Homework_Assignments/
│   └── Individual assignments covering EDA, regression, and model evaluation
├── Group_Project_Zillow_Housing_Dataset/
│   └── Team project: predicting home tax-assessed value
└── README.md
```

## [Homework Assignments](./Homework_Assignments)

Individual assignments completed throughout the course. Topics covered:
- Data cleaning and preprocessing
- Exploratory Data Analysis (EDA)
- Linear regression
- Polynomial regression
- Train/test splitting and model selection
- Feature engineering and feature selection
- Decision tree models
- Model evaluation using performance metrics

*(Note: double check this list against what's actually in the folder before publishing — swap in the real assignment titles if they differ from the general topics above.)*

## [Group Project: Zillow Housing Price Prediction](./Group_Project_Zillow_Housing_Dataset)

A team project using the Zillow housing dataset, following the full ML workflow:
1. Problem definition
2. Data exploration
3. Data cleaning and preprocessing
4. Feature relationship analysis
5. Feature engineering
6. Model development and evaluation
7. Final model selection and presentation

See the [project README](./Group_Project_Zillow_Housing_Dataset/README.md) for the full technical writeup, results table, and methodology.

## How to Run

```bash
pip install -r requirements.txt
jupyter lab
```

*(Verify `requirements.txt` exists in the repo root before publishing this — if it's missing, generate one with `pip freeze > requirements.txt` from your project's environment, or I can build one from the notebook imports.)*

## Purpose

This repository demonstrates applied machine learning skills — from raw data through a tuned, evaluated model — across both individual coursework and a collaborative team project using Python and Jupyter.
