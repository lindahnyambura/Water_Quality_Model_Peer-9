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
- This model has been developed in four iterations, which have seen the model give different results each time.
- Each iteration maintains the same optimizer (**RMSprop with a learning rate of 0.0005**), progressively decreasing Dropout rates (**0.3, 0.2, 0.1**) to control overfitting, and Early stopping (patience = 10) ensuring the model doesn’t stop training too early
  1. The initial model had a 64-32-16 architecture and had the worst performance, with an accuracy of 62%, and a Class 1 recall of 0% meaning it failed to predict potable water and was **highly biased** toward Class 0
  2. The next model had more neurons (128-64-32) and only from that change accuracy improved to 68% with the Class 1 recall increasing to 39%. However, **false positives increased**, meaning that some class 0s (non-potable water) were misclassified as potable.
  3. The third iteration focuses on fixing the class imbalance seen, so the threshold is lowered from 0.5 to 0.4, and class weights (2 for Class 1) are introduced. Class 1 recall increased to 84% and its precision dropped to 45%. It is observed that the model was **over-predicting** potable water
  4. The final iteration adjusts class weight to 1.2 and threshold to 0.45. The model scores an accuracy of 66%, and balances recall and precision better than the previous models Recall: Class 0 = 0.76, Class 1 = 0.49 Precision: Class 0 = 0.71, Class 1 = 0.55. The threshold found the best tradeoff between capturing potable water and avoiding excessive false positives.


### 2. Kevin Kenny Mugisha (Adam + Early stopping + Dropout + Batch Normalization)

My model is made by 3 hidden layers with 20 neurons, relu activation, Batch normalization after each layer for stability and dropout of 0.2 to prevent overfitting and it has 1 output layer with sigmoid activation. I applied some optimization techniques to my model such as Adam with a learning rate of 0.0001 which happened to give me a stable convergence, for loss function I used Binary crossentropy and metrics I used Accuracy, Precision and recall. For regularization techniques I used Dropout of 0.2 on each layer and early stopping that monitors "val_loss" and has patience of 50 epochs. I used 1000 epochs, 64 batch size and validation data to track the performance and I did evaluation of loss and accuracy by ploting them to see the difference btn train and validation data how the model performed to them.
So after 9 trials this model with all those things I mentioned performed better than other I did in trials and it has an accurracy of 70%, 1-score of 79%(0) and 44%(1), Precision of 69%(0) and 71%(1), recall of 92%(0) and 32%(0).

### 3. Valentine Kalu (...)

## Model Comparisons

### Lindah vs Kenny
| **Feature**             | **Lindah's Model**                    | **Kenny's Model**                     |
|-------------------------|---------------------------------------|---------------------------------------|
| **Architecture**        | 3 layers (128-64-32)                  | 3 layers (20-20-20)                   |
| **Activation**          | ReLU                                  | ReLU                                  |
| **Batch Normalization** | No                                    | Yes (After each layer)                |
| **Dropout**             | 0.3 → 0.2 → 0.1                       | 0.2 (All layers)                      |
| **Optimizer**           | RMSprop (LR = 0.0005)                 | Adam (LR = 0.0001)                    |
| **Loss Function**       | Binary Crossentropy                   | Binary Crossentropy                   |
| **Metrics**             | Accuracy, Precision, Recall, F1       | Accuracy, Precision, Recall, F1       |
| **Regularization**      | Dropout, Early Stopping (patience=10) | Dropout, Early Stopping (patience=50) |
| **Class Weights**       | Yes (1.2 for Class 1)                 | No                                    |
| **Epochs & Batch Size** | Up to 100 (Early Stopping)            | 1000 epochs, Batch size = 64          |
| **Threshold**           | 0.45 (Custom)                         | 0.5 (Default)                         |
| **Final Accuracy**      | 66%                                   | 70%                                   |
| **F1 Score**            | Class 0: 74%, Class 1: 52%            | Class 0: 79%, Class 1: 44%            |
| **Precision**           | Class 0: 71%, Class 1: 55%            | Class 0: 69%, Class 1: 71%            |
| **Recall**              | Class 0: 76%, Class 1: 49%            | Class 0: 92%, Class 1: 32%            |

#### Insights
- Kenny's model has a higher overall accuracy (70%), likely due to batch normalization and Adam optimizer with a very low learning rate (0.0001)
- Kenny’s model is very strong at identifying non-potable water (Higher class 0 recall of 92%)
- When Kenny’s model predicts potable water, it is more likely correct (71%) than Lindah's (55%).
- As F1 score balances precision and recall, Lindah's model is better at consistently identifying potable water (52% vs 44%) likely due to Lindah's approach to addressing class imbalance
- Lindah's model identifies more potable water samples correctly (Higher recall for class 1: 49% vs. 32%). Kenny’s model is missing a lot of potable water cases (high false negatives)
- Lindah's model has a better balance between precision and recall. Kenny’s model overemphasized non-potable water, making it conservative in predicting potable water.


### Lindah vs Valentine

### Kenny vs Valentine

### Results & Insights

Each model is compared based on F1 score, precision, recall, and loss. Key findings and performance differences are documented.

(0) - Class 0 (non-potable)

(1) - Class 1 (potable)

| **Train Instance** | **Engineer Name** | **Regularizer**             | **Optimizer** | **Early Stopping**            | **Dropout Rate** | **Accuracy** | **F1 Score**     | **Recall**       | **Precision**    |
| ------------------ | ----------------- | --------------------------- | ------------- | ----------------------------- | ---------------- | ------------ | ---------------- | ---------------- | ---------------- |
|                    | Lindah Nyambura   | Dropout                     | RMSprop       | patience=10, monitor=val_loss| 0.3 → 0.2 → 0.1  | 66%          | 0.74(0), 0.52(1) | 0.76(0), 0.49(1) | 0.71(0), 0.55(1) |
|                    | Valentine Kalu    |                             |               |                               |                  |              |                  |                  |                  |
|                    | Kevin Mugisha     | Dropout, BatchNormalization | Adam          | patience=50, monitor=val_loss | 0.2              | 70%          | 79%(0), 44%(1)   | 92%(0), 32%(1)   | 69%(0), 71%(1)   |
