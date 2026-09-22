# Dataset

This directory contains the Ethereum transaction data used in the experimental pipeline.

The dataset consists of **88,145 Ethereum transactions** collected from Etherscan and subsequently processed for anomaly detection experiments.

The data are organized into two groups:

```text
data/
├── source/
│   ├── 01_ethereum_raw.csv
│   └── 02_ethereum_parsed.csv
└── splits/
    ├── 11_train.csv
    ├── 12_validation.csv
    ├── 13_calibration.csv
    └── 14_holdout_test.csv
```

## Source and Intermediate Data

### `01_ethereum_raw.csv`

Raw Ethereum transaction dataset collected from Etherscan.

This file serves as the starting point for the **Full Run** scenario in the notebook.

### `02_ethereum_parsed.csv`

Intermediate dataset obtained after the initial parsing and data-cleaning stage.

It is used as a prepared intermediate artifact and can also be loaded directly when reproducing selected downstream analyses.

## Prepared Data Splits

The processed dataset is divided into four non-overlapping subsets with different roles in the experimental pipeline.

| File | Subset | Number of transactions | Purpose |
|---|---|---:|---|
| `11_train.csv` | Train | 60,725 | Training the autoencoder on normal transactions only |
| `12_validation.csv` | Validation | 13,013 | Training monitoring, early stopping, and heuristic threshold estimation |
| `13_calibration.csv` | Calibration | 7,203 | Model comparison and optimized threshold selection |
| `14_holdout_test.csv` | Holdout Test | 7,204 | Final evaluation after model architecture, hyperparameters, and threshold have been fixed |

The **Train** subset contains only normal transactions (`label = 0`), because the autoencoder is trained to reconstruct normal transaction behavior.

Fraud labels are not used during autoencoder training. They are used at later stages for threshold calibration, model comparison, and final evaluation.

The **Holdout Test** subset is kept separate from model selection and threshold calibration and is used only for the final evaluation of the selected model.

## Reproducibility

The notebook supports two execution scenarios:

- **Full Run** — starts from `01_ethereum_raw.csv` and reproduces the complete preprocessing, feature engineering, model training, calibration, and evaluation pipeline.
- **Fast Run** — uses prepared datasets and other saved artifacts to reproduce selected analyses without retraining the complete pipeline.

The prepared splits provided in this directory correspond to the experimental setup used in the accompanying research work.

## Dataset Usage

The dataset was collected from publicly accessible Ethereum transaction information available through Etherscan.

The software license of this repository does not automatically define the usage terms of the underlying dataset. Dataset usage conditions should therefore be considered separately from the source-code license.
