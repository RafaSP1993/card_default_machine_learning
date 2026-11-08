# Credit card default prediction (Taiwan, 2005)

*[Versión en español](README_es.md)*

Predicts whether a credit card client will default next month, using six months of payment history. Educational portfolio project.

## Results

Test set of 6,000 clients the model never saw:

| Model | ROC-AUC | PR-AUC |
|---|---|---|
| Logistic regression | 0.764 | 0.526 |
| **Random Forest** (final model) | **0.779** | **0.566** |

With a 0.29 threshold (maximum F1), the Random Forest detects **56% of defaults** (741 of 1,327) and flags **14% of good clients** by mistake (666 of 4,673).

## Key findings

- **Demographics matter little.** Default varies by education, age, sex and marital status, but the differences are small.
- **Recent payment behaviour is the best predictor**, especially the delay in the last month.
- **The Random Forest beats the logistic regression only slightly**, mostly among the riskiest clients.

## Structure

```
cardDefaultML/
├── UCI_Credit_Card.csv        not included, see "How to run"
├── requirements.txt
├── cardDefault_ENG/          English notebooks
│   ├── 01_EDA_CC.ipynb         cleaning, EDA and feature engineering
│   ├── 02_Modeling_CC.ipynb    model training and selection
│   └── 03_Evaluation_CC.ipynb  threshold, calibration, test and conclusions
└── cardDefault_SP/           same notebooks in Spanish
```

Run the notebooks in order: 01 → 02 → 03.

## How to run

1. Download `UCI_Credit_Card.csv` from [Kaggle](https://www.kaggle.com/datasets/uciml/default-of-credit-card-clients-dataset) and put it in the root folder, next to `requirements.txt`. The dataset is not included in this repository.
2. Install the dependencies (tested with Python 3.13) and open Jupyter:

```bash
pip install -r requirements.txt
jupyter notebook
```

## Limitations

- Data from 2005 and a single market (Taiwan).
- No income or employment data.
- The model uses sex, age and marital status, which many jurisdictions forbid in credit decisions. It is not ready for real use.

## Data

Yeh, I. (2009). *Default of Credit Card Clients*. [UCI Machine Learning Repository](https://doi.org/10.24432/C55S3H). License: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
