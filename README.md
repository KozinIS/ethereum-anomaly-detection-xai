# Explainable Autoencoder for Ethereum Anomaly Detection

An explainable anomaly detection framework for Ethereum transactions based on an autoencoder with an attention mechanism and SHAP-based interpretation.

The repository contains the reproducible Proof of Concept accompanying the research paper. The notebook implements the complete experimental pipeline, including data preprocessing, autoencoder architecture comparison, threshold calibration, explainability analysis, comparison with alternative anomaly detection methods, and final holdout evaluation.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/KozinIS/ethereum-anomaly-detection-xai/blob/main/notebooks/ethereum_anomaly_detection_xai_RU.ipynb)


## Quick Start

The recommended way to reproduce the experiments is Google Colab.

1. Click the **Open in Colab** button above.
2. Run the notebook from the beginning using **Runtime → Run all**.
3. Leave `SAVE_ARTIFACTS = False` for the standard reproducible run.
4. Set `SAVE_ARTIFACTS = True` only if you want generated datasets, trained models, and experimental artifacts to be saved to your Google Drive.

The notebook downloads the required public repository data and artifacts directly from GitHub. Google Drive access is not required unless artifact saving is explicitly enabled.

Two execution scenarios are supported:

- **Full Run** — reproduces the complete experimental pipeline from the raw Ethereum transaction dataset.
- **Fast Run** — uses the prepared datasets, pretrained models, and saved experimental artifacts provided in Appendix B of the notebook.

> **Note:** The notebook was developed and tested primarily in Google Colab. Reproducing the full training pipeline may require substantial execution time.


## Repository Structure

```text
ethereum-anomaly-detection-xai/
├── data/
│   ├── source/                 # Raw and parsed Ethereum transaction data
│   └── splits/                 # Train, validation, calibration, and holdout test sets
├── preprocessing/              # Preprocessing artifacts and fitted scaler
├── models/
│   ├── autoencoders/           # Trained autoencoder models
│   └── alternative_methods/    # Isolation Forest, LOF, and VAE artifacts
├── results/
│   ├── training_history/
│   ├── shap/
│   ├── attention/
│   ├── explainability_comparison/
│   ├── alternative_methods/
│   └── model_6_analysis/
└── notebooks/
    └── ethereum_anomaly_detection_xai_RU.ipynb
```


## Dataset

The repository contains a dataset of Ethereum transactions collected from Etherscan and the derived datasets used in the experiments.

The experimental pipeline separates the data into four subsets:

Train — used to train the autoencoder on normal transactions only.
Validation — used for training monitoring, early stopping, and heuristic threshold estimation.
Calibration — used for model comparison and optimized threshold selection.
Holdout Test — used only for the final evaluation after the model architecture and threshold have been fixed.

Additional information about the dataset files is provided in data/README.md.


## Environment

The notebook was developed and tested primarily in Google Colab.

Main environment:

Python 3.12
TensorFlow 2.20
NumPy
pandas
scikit-learn
SHAP
SciPy
Matplotlib


## Research Paper

This repository accompanies the research paper describing the proposed anomaly detection and explainability framework.

A link to the preprint will be added after publication on arXiv.
