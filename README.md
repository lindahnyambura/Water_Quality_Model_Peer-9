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

## Experiments & Comparisons

### Model Summaries

### 1. Lindah Nyambura (RMSprop + Dropout)

### 2. Kevin Kenny Mugisha (Adam + Early stopping + Dropout + Batch Normalization)

My model is made by 3 hidden with 20 neurons, relu activation, Batch normalization after each layer for stability and dropout of 0.2 to prevent overfitting and it has 1 output layer with sigmoid activation. I applied some optimization techniques to my model such as Adam with a learning rate of 0.0001 which happened to give me a stable convergence, for loss function I used Binary crossentropy and metrics I used Accuracy, Precision and recall. For regularization techniques I used Dropout of 0.2 on each layer and early stopping that monitors "val_loss" and has patience of 50 epochs. I used 1000 epochs, 64 batch size and validation data to track the performance and I did evaluation of loss and accuracy by ploting them to see the difference btn train and validation data how the model performed to them.
So after 9 trials this model with all those things I mentioned performed better than other I did in trials and it has an accurracy of 70%, 1-score of 79%(0) and 44%(1), Precision of 69%(0) and 71%(1), recall of 92%(0) and 32%(0).

### 3. Valentine Kalu (...)

## Model Comparisons

### Lindah vs Kenny

### Lindah vs Valentine

### Kenny vs Valentine

### Results & Insights

Each model is compared based on F1 score, precision, recall, and loss. Key findings and performance differences are documented.

| **Train Instance** | **Engineer Name** | **Regularizer**             | **Optimizer** | **Early Stopping**            | **Dropout Rate** | **Accuracy** | **F1 Score**     | **Recall**       | **Precision**    |
| ------------------ | ----------------- | --------------------------- | ------------- | ----------------------------- | ---------------- | ------------ | ---------------- | ---------------- | ---------------- |
|                    | Lindah Nyambura   | Dropout                     | RMSprop       | ✅ patience=10                | 0.3 → 0.2 → 0.1  | 66%          | 0.74(0), 0.52(1) | 0.76(0), 0.49(1) | 0.71(0), 0.55(1) |
|                    | Valentine Kalu    |                             |               |                               |                  |              |                  |                  |                  |
|                    | Kevin Mugisha     | Dropout, BatchNormalization | Adam          | patience=50, monitor=val_loss | 0.2              | 70%          | 79%(0), 44%(1)   | 92%(0), 32%(1)   | 69%(0), 71%(1)   |
