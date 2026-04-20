# Evaluate Student Writing using Machine Learning

This project builds a multi-class machine learning system to classify discourse segments in student essays from the Feedback Prize 2021 dataset. The task is to predict one of seven discourse types such as Lead, Claim, Evidence, Rebuttal, and Concluding Statement.

## Project Overview

The project uses the Kaggle **Feedback Prize - Evaluating Student Writing** dataset, which contains argumentative essays and labeled discourse spans. The goal is to classify each discourse span into its correct discourse category.

This project combines:

- **TF-IDF text features**
- **Engineered structural features**
- **Grouped cross-validation** to avoid essay-level data leakage
- **Macro F1** as the main evaluation metric because the dataset is imbalanced

## Dataset

- Source: Kaggle Feedback Prize 2021
- Data includes student essays and labeled discourse spans
- Target variable: `discourse_type`

### Discourse Classes
- Lead
- Position
- Claim
- Counterclaim
- Rebuttal
- Evidence
- Concluding Statement

## Methods Used

### Text Features
- TF-IDF vectorization
- Unigrams and bigrams

### Engineered Features
- Relative position in essay
- Word count
- Character length
- Sentence count
- Essay length
- Normalized rank
- Position bucket
- Signal-word-based feature

### Models Compared
- Dummy Classifier
- Logistic Regression
- Linear SVM
- Random Forest

## Evaluation Strategy

To prevent data leakage, the project uses **GroupKFold cross-validation** grouped by essay ID.

Since the class distribution is imbalanced, **Macro F1** is used as the primary metric instead of accuracy.

## Results

### Final Model Comparison

| Model | Macro F1 | Accuracy | Macro Precision | Macro Recall |
|---|---:|---:|---:|---:|
| Logistic Regression (TF-IDF + Engineered) | 0.7406 | 0.8310 | 0.8002 | 0.7164 |
| Linear SVM (TF-IDF + Engineered) | 0.7148 | 0.7981 | 0.7521 | 0.6916 |
| Random Forest (Structural) | 0.6023 | 0.7757 | 0.6439 | 0.6015 |
| Dummy Baseline | 0.0743 | 0.3512 | 0.0502 | 0.1429 |

### Best Model
**Logistic Regression with TF-IDF + engineered features** performed best on the test set.

- **Macro F1:** 0.7406
- **Accuracy:** 0.8310

### Key Findings
- Combining lexical and structural features improved performance significantly
- Position-related features were highly informative
- The model performed best on structured classes like **Lead** and **Concluding Statement**
- Minority classes such as **Counterclaim** and **Rebuttal** were harder to predict

## Subgroup Analysis

Performance varied across essay and span lengths:

### Macro F1 by Essay Length
- Short essays: **0.6733**
- Medium essays: **0.7373**
- Long essays: **0.7876**

### Macro F1 by Span Length
- Short spans: **0.6314**
- Medium spans: **0.6812**
- Long spans: **0.5751**

This suggests the model performs better when there is enough contextual information.

## Repository Structure

```text
.
├── README.md
└── evaluate-student-writing.ipynb
