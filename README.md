# Algorithmic Fairness - Reweighing

This repository contains the Python notebook for Assignment 4 on Algorithmic Fairness. The project evaluates the Reweighing bias-mitigation algorithm introduced by Kamiran and Calders.

## Method

Reweighing is a pre-processing bias-mitigation method that assigns different weights to training observations based on their protected group and class label. The original features and labels are not changed.

## Datasets

The algorithm is evaluated on three publicly available datasets:

- Adult Census Income
- German Credit
- COMPAS

Protected attributes:
- Adult: `sex`
- German Credit: `sex`
- COMPAS: `race`

## Evaluation

Fairness is evaluated using:

- Demographic Parity Difference (DP_Diff)
- Disparate Impact Ratio (DIR)
- Consistency

Predictive performance is evaluated using Accuracy, Balanced Accuracy and F1-score.

## Experimental setup

- Bias-mitigation algorithm: Reweighing
- Classifier: Logistic Regression
- Train/test split: 70/30
- Random state: 42
- Stratification: class label + protected group
- Consistency neighbours: 5
- Logistic Regression solver: `liblinear`
- Maximum iterations: 1000
- Reweighing is applied to the training data only

## Results

| Dataset | DP_Diff Before | DP_Diff After | DIR Before | DIR After | Consistency Before | Consistency After | Accuracy |
|---|---:|---:|---:|---:|---:|---:|---:|
| Adult | -0.1989 | -0.1001 | 0.3635 | 0.5443 | 0.8035 | 0.9482 | 0.8444 |
| German Credit | -0.0748 | -0.0117 | 0.8966 | 0.9845 | 0.6788 | 0.7733 | 0.7633 |
| COMPAS | -0.1321 | -0.2354 | 0.7830 | 0.6762 | 0.5992 | 0.8680 | 0.6618 |

Reweighing improved demographic parity for Adult and German Credit. For COMPAS, consistency improved while DP_Diff and DIR became less favorable, showing that mitigation does not necessarily improve every fairness measure on every dataset.

## Requirements

Install the required packages with:

`pip install aif360 pandas numpy scikit-learn matplotlib seaborn`

## Running the notebook

Open `Task_2_Reweighing_Evaluation_Kadir_Gunduz.ipynb` in Jupyter Notebook or Visual Studio Code and run all cells from top to bottom.
