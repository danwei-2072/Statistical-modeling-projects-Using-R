# Predictive Modeling and Method Comparison

## Project Overview

This project aims to explore the `Residen.RData` dataset and compare various statistical modeling methods for predicting the target variable `V104`. The project covers the entire process from data exploration and preprocessing to model building, evaluation, and comparison.

Key objectives include:

1.  Performing exploratory data analysis (EDA) to understand variable relationships.
2.  Identifying and addressing potential multicollinearity issues.
3.  Applying and comparing the following modeling methods:
    *   Multiple Linear Regression (Full Model)
    *   Stepwise Regression (Backward, Both Directions)
    *   Ridge Regression
    *   LASSO Regression (Least Absolute Shrinkage and Selection Operator)
4.  Evaluating model performance using hold-out validation and cross-validation.
5.  Conducting a comprehensive comparison based on predictive accuracy (MSE), model complexity, interpretability, and computational efficiency.

## Dataset

The dataset used in this project is `Residen.RData`.
*Please ensure this dataset file is located in the same working directory as the R code file or is accessible by the R environment.* (Modify this sentence if `Residen.RData` is included in the repository, e.g., "The dataset `Residen.RData` is included in this repository.")

## File Structure

*   `Statistical_modeling_projects_using_R.Rmd`: Contains the R Markdown source code for all analysis steps, model building, and evaluation.
*   `Statistical_modeling_projects_using_R.pdf`: The report document generated from the R Markdown file, including code, output, plots, and analysis explanations.
*   `README.md`: This file, providing an overview and instructions for the project.
*   `Residen.RData`: The dataset file.

## Analysis Methods & Steps

1.  **Environment Setup:** Install and load required R packages (`corrplot`, `plotly`, `caret`, `MASS`, `glmnet`, `leaps`).
2.  **Data Loading & Exploration:** Load the `Residen.RData` dataset, compute the correlation matrix, and visualize the correlation heatmap using `plotly`.
3.  **Data Preprocessing:**
    *   Remove a specific column (column 109) from the dataset.
    *   Split the dataset into training (80%) and testing (20%) sets.
4.  **Initial Linear Model:** Build a multiple linear regression model using all predictors and analyze its coefficients, significance, and multicollinearity issues (indicated by `NA` coefficients and warnings).
5.  **Variable Selection - Stepwise Regression:**
    *   Apply AIC-based backward stepwise regression (`direction = "backward"`).
    *   Apply AIC-based bidirectional stepwise regression (`direction = "both"`).
    *   Record and compare the computation time for both methods.
6.  **Regularization Methods:**
    *   **Ridge Regression:** Use `cv.glmnet` with cross-validation to select the optimal lambda (alpha=0) and build the Ridge model.
    *   **LASSO Regression:** Use `cv.glmnet` with cross-validation to select the optimal lambda (alpha=1) and build the LASSO model.
    *   Record and compare the computation time for both regularization methods.
7.  **Model Evaluation:**
    *   Calculate the Mean Squared Error (MSE) on the test set for the stepwise, Ridge, and LASSO models.
    *   Evaluate the performance of the stepwise regression models using 10-fold cross-validation (calculate CV MSE).
8.  **Results Comparison & Discussion:**
    *   Compare the performance of different models based on test set MSE and (for some models) CV MSE.
    *   Discuss model fit metrics like R-squared, Adjusted R-squared, and Residual Standard Error.
    *   Analyze model complexity (number of variables), interpretability, and computational efficiency.
    *   Summarize the pros and cons of each method and provide recommendations based on analysis goals.

## Key Findings

*   The initial full linear model suffered from severe multicollinearity, making some coefficients inestimable.
*   Stepwise regression methods effectively selected variable subsets, improving model stability and interpretability, but were computationally expensive, especially bidirectional stepwise.
*   Ridge and LASSO regression were computationally efficient and effectively handled multicollinearity.
*   LASSO regression performed built-in variable selection, resulting in a sparser (simpler) model.
*   In the test set evaluation for this project, Ridge regression achieved a slightly lower prediction error (MSE) compared to LASSO and stepwise methods. Cross-validation evaluation favored the bidirectional stepwise model.
*   The choice of model involves a trade-off between predictive accuracy, interpretability, complexity, and computational resources.

## Software & R Packages

*   **R:** The project code was run successfully on R version 4.2.3 (as indicated in the PDF output).
*   **RStudio:** (Recommended) As an integrated development environment for R.
*   **R Packages:**
    *   `corrplot`
    *   `plotly`
    *   `caret`
    *   `MASS`
    *   `glmnet`
    *   `leaps`

## How to Run

1.  Clone or download this repository.
2.  Ensure the `Residen.RData` dataset file is in the R working directory (or modify the file path in the code if it's elsewhere).
3.  Open the `STAT448_Assignment2.Rmd` (or `.R`) file in RStudio.
4.  If the required R packages are not already installed, run the following command in the R console:
    ```R
    install.packages(c("corrplot", "plotly", "caret", "MASS", "glmnet", "leaps"))
    ```
5.  Run the code chunks in the R Markdown file sequentially (or simply click the "Knit" button to generate the PDF report) to reproduce the entire analysis.
