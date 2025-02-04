# Water Quality Model

## Project Overview

This project aims to build a binary classification model to predict water potability based on various water quality parameters. Each team member applies a unique combination of regularization and optimization techniques to explore how different configurations impact model performance.

## Dataset

We use the Water Quality and Potability dataset from [Kaggle](https://www.kaggle.com/datasets/uom190346a/water-quality-and-potability?select=water_potability.csv), which contains:

- 9 features such as pH, Hardness, Solids, Chloramines, Sulfate, Conductivity, Organic Carbon, Trihalomethanes, and Turbidity.
- Target Variable: Potability (0 = Not Potable, 1 = Potable)

## Model Approach

Each model variation follows these key components:

### Preprocessing Steps

- Handling missing values (imputation)
- Scaling/normalizing features

### Model Architecture & Training

- Different combinations of optimizers, regularization techniques, and early stopping criteria.
- Metrics used: F1 Score, Precision, Recall, Loss

### Experiments & Comparisons

Each team member tries a unique combination of:

- .
-
-

### Results & Insights

Each model is compared based on F1 score, precision, recall, and loss. Key findings and performance differences are documented.

| **Train Instance** | **Engineer Name** | **Regularizer**             | **Optimizer** | **Early Stopping** | **Dropout Rate**      | **Accuracy** | **F1 Score**     | **Recall**       | **Precision**    |
| ------------------ | ----------------- | --------------------------- | ------------- | ------------------ | --------------------- | ------------ | ---------------- | ---------------- | ---------------- |
|                    | Lindah Nyambura   | Dropout                     | RMSprop       | ✅ patience=10     | 0.3 → 0.2 → 0.1       | 65%          | 0.72(0), 0.52(1) | 0.73(0), 0.51(1) | 0.71(0), 0.53(1) |
|                    | Valentine Kalu    |                             |               |                    |                       |              |                  |                  |                  |
|                    | Kevin Mugisha     | Dropout, BatchNormalization | Adam          | patience=50        | 0.3 → 0.2 → 0.1 → 0.2 | 70%          | 79%(0), 44%(1)   | 92%(0), 32%(1)   | 69%(0), 71%(1)   |

## How to Run the Project

## Contributors
