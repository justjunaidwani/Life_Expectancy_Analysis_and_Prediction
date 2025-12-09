# Life Expectancy Analysis and Prediction

## Project Overview

This data science project focuses on exploring global life expectancy data to identify key socio-economic and health factors that influence the life expectancy of countries. The ultimate goal is to build a robust regression model capable of predicting a country's life expectancy based on various input features.

## Data Source

The project uses the `Life Expectancy Data.csv` dataset.
* **Initial Shape:** The dataset contains 2,938 rows and 22 columns.
* **Target Variable:** The primary variable for prediction is `Life expectancy`.

## Table of Contents

1.  [Data Processing and Cleaning](#data-processing-and-cleaning)
2.  [Exploratory Data Analysis (EDA) - Key Findings](#exploratory-data-analysis-eda---key-findings)
3.  [Modeling and Results](#modeling-and-results)
4.  [Setup and Installation](#setup-and-installation)
5.  [Project Structure](#project-structure)

## Data Processing and Cleaning

The initial data required extensive cleaning and preprocessing to prepare it for modeling:

### 1. Missing Value Imputation
* A small percentage of rows containing null values in crucial columns (`Life expectancy`, `Adult Mortality`, `Polio`, `BMI`, `Diphtheria`, `thinness 1-19 years`, `thinness 5-9 years`) were dropped.
* The remaining missing values in columns such as `Alcohol`, `Hepatitis B`, `Total expenditure`, `GDP`, `Population`, `Income composition of resources`, and `Schooling` were imputed using the **KNN Imputer** technique.

### 2. Outlier Handling
* Outliers were detected in multiple columns, including `Adult Mortality`, `infant deaths`, `Alcohol`, `Measles`, and `HIV/AIDS`.
* These outliers were handled using the **Interquartile Range (IQR) Outlier Capping** technique to preserve most of the data and prevent information loss. *The `Life expectancy` column's outliers were preserved since it is the target variable*.

### 3. Feature Scaling and Encoding
* The categorical `Status` column (`Developing`, `Developed`) was processed using **Ordinal Encoding**.
* The `Country` column was handled with **OneHotEncoder**.
* All remaining numerical columns were standardized using the **StandardScaler** to ensure equal contribution during model training.

## Exploratory Data Analysis (EDA) - Key Findings

* **Development Status:** The average life expectancy is significantly higher in **Developed** countries (mean: ~79.2) compared to **Developing** countries (mean: ~67.2).
* **Mortality:** Both **Adult Mortality** and **Infant Deaths** rates are considerably lower in Developed Countries compared to Developing Countries.

## Modeling and Results

A baseline Linear Regression model and a Ridge Regression model were trained, but the best performance was achieved using a **Support Vector Regressor (SVR)**.

### Model Performance (SVR)

| Metric | Score | Note |
| :--- | :--- | :--- |
| Training Accuracy | 0.961 | |
| Testing Accuracy (Cross-validation) | 0.959 | |

The high and closely matched training and testing scores indicate that the SVR model generalizes well and shows no significant signs of overfitting.

## Setup and Installation

To run the Jupyter notebook (`Analysis and Model Building.ipynb`), you will need the following libraries:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn


## Project Structure


├── Analysis and Model Building.ipynb # Main analysis and modeling notebook

├── Life Expectancy Data.csv          # The dataset used for the project

└── README.md