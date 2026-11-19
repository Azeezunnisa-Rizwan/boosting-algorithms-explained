# Boosting Algorithms Explained

My notes and code from learning boosting: how AdaBoost, gradient boosting and XGBoost work, worked by hand first and then run in scikit-learn and XGBoost.

## What's inside

| Folder | Contents |
|---|---|
| `adaboost/` | Step-by-step walkthrough of AdaBoost (sample weights, tree significance, weight updates), then a scikit-learn run on the breast cancer dataset |
| `gradient-boosting/` | Gradient boosting for regression, with an Excel worked example and a `GradientBoostingRegressor` run on housing data |
| `xgboost/` | Gradient boosting vs XGBoost on the breast cancer dataset |
| `notes/` | Whiteboard and Excel notes: boosting math, gradient boosting classification, XGBoost similarity score and gain, algorithm comparison |

## The three algorithms in short

- **AdaBoost** trains one-split trees (stumps) in a row. After each tree it raises the weight of the samples it got wrong, so the next tree focuses on them.
- **Gradient boosting** starts from an average prediction, then fits each new tree to the previous residuals. A learning rate keeps each step small.
- **XGBoost** follows the same idea but picks splits with a similarity score and gain, and adds regularization (lambda) and pruning (gamma).

## Results

| Notebook | Dataset | Result |
|---|---|---|
| AdaBoost classifier | Breast cancer (569 rows) | 96.5% test accuracy (138 of 143). 2 benign cases flagged malignant, 3 malignant missed |
| Gradient boosting regressor | Boston housing | Test MAE of about 3.06 (house prices in $1,000s) |
| Gradient boosting vs XGBoost | Breast cancer (114 test rows) | Both 95.6% accuracy. Gradient boosting missed 2 malignant cases, XGBoost missed 5 |

The two classifiers tie on accuracy. With only 114 test rows, a gap of a few samples is noise, so I don't read it as one model being better.

## Run it

Install the libraries with `pip install scikit-learn xgboost pandas jupyter`, then open the notebooks with Jupyter.

No CSV files are needed because the datasets load from scikit-learn. The Boston housing notebook was run on an older scikit-learn version, since newer versions removed that dataset.

## Sources

The step-by-step explanations and some diagrams are adapted from public articles. The whiteboard and Excel notes are from a data science course I took.
