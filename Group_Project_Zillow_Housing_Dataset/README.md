***MUST EDIT***
# Zillow Housing Price Prediction Project

## Overview

This project applies machine learning techniques to predict property values using a subset of the Zillow housing dataset. The goal is to predict the assessed tax value (`taxvaluedollarcnt`) of properties based on available property characteristics and to investigate how data cleaning, feature engineering, feature selection, and model tuning affect predictive performance.

This project was completed as part of a Machine Learning Fundamentals course and follows a structured data science workflow:

1. Understanding and exploring the dataset
2. Cleaning and preparing the data
3. Exploring feature relationships
4. Engineering new features
5. Building and evaluating machine learning models
6. Selecting and tuning the best-performing model

## Dataset

The dataset is a smaller version of the Zillow housing dataset originally used in the Zillow Prize Kaggle competition.

The target variable is:

* `taxvaluedollarcnt` — assessed tax value of the property

The dataset contains property characteristics such as:

* Square footage
* Number of bedrooms and bathrooms
* Year built
* Lot size
* Room counts
* Other property descriptors

The dataset includes missing values, outliers, and features with varying usefulness, requiring preprocessing before modeling.

## Project Structure

```
Group_Project_Zillow_Housing_Dataset/
│
├── Diagrams/
│
├── Project_Milestone_One_Zillow_EDA/
│   └── Exploratory data analysis and initial data preparation
│
├── Project_Milestone_Two_Modeling_Feature_Engineering/
│   └── Model comparison, feature engineering, and optimization
│
├── Zillow_Final_Report/
│   └── Final technical report and project conclusions
│
├── Zillow_Housing_Project_Presentation/
│   └── Final presentation PDF
│
├── zillow_cleaned.csv
│   └── Cleaned dataset used for modeling
│
└── README.md
```

## Milestone 1: Data Exploration and Preparation

The first milestone focused on understanding the dataset and preparing it for modeling.

Work completed:

* Loaded and examined the Zillow dataset
* Performed exploratory data analysis (EDA)
* Investigated feature distributions and outliers
* Analyzed missing values
* Removed unsuitable features
* Imputed missing values
* Investigated feature relationships using correlations and feature selection methods
* Explored possible feature engineering approaches

## Milestone 2: Modeling and Feature Engineering

The second milestone focused on developing predictive models and improving performance.

Work completed:

* Established baseline regression models
* Tested different machine learning algorithms
* Evaluated models using performance metrics
* Applied feature engineering techniques
* Investigated feature selection methods
* Tuned promising models to improve predictive accuracy

## Final Report

The final report summarizes:

* The selected final model
* Data preparation decisions
* Feature engineering choices
* Model evaluation results
* Lessons learned and possible improvements

## Presentation

The final presentation provides a simplified overview of the project for a general audience, focusing on:

* The problem being solved
* Dataset insights
* Modeling approach
* Results and conclusions

## Team Members

(Add team member names here)

## Tools and Technologies

The project uses:

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
* Jupyter Notebook

## Conclusion

This project demonstrates the end-to-end machine learning workflow for a real-world housing prediction problem, including data exploration, preprocessing, feature engineering, model development, and evaluation.


This repository contains homeworks posted for student downloads in Module 3 of DS 603 in Spring 2025. 
