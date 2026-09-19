# Machine Learning-Based Network Intrusion Detection System

An end-to-end machine learning project for detecting malicious network traffic using the CICIDS2017 dataset.

**Author:** João Bernardo Sousa Faria

## Overview

This project develops and evaluates a binary network intrusion detection pipeline that classifies network flows as benign or malicious. It compares interpretable baselines with ensemble and gradient-boosting models, then examines how well the models generalize to traffic from an unseen source file.

The workflow covers data ingestion, cleaning, feature preparation, model training, threshold tuning, explainability, cross-validation, multiclass experimentation, and source-based holdout evaluation.

## Models

- Dummy classifier baseline
- Rule-based detection baseline
- Logistic Regression
- Random Forest
- Tuned Random Forest
- Histogram-based Gradient Boosting

## Key Results

The best binary classifier was Histogram-based Gradient Boosting.

| Evaluation | Accuracy | Attack precision | Attack recall | Attack F1 |
|---|---:|---:|---:|---:|
| Random test split | 0.9986 | 0.9948 | 0.9957 | 0.9953 |
| 3-fold cross-validation | - | - | - | 0.9917 |
| Source-file holdout | 0.8955 | 0.9964 | 0.6079 | 0.7551 |

The strong random-split result shows that the model can accurately separate benign and malicious flows within the sampled distribution. The lower source-file holdout recall highlights a more realistic challenge: detecting attacks when network conditions and traffic sources change.

## Dataset

The project uses CICIDS2017 network-flow data from eight CSV files. A reproducible sample of 300,000 flows was used for experimentation, with 69 numerical features and 15 original traffic labels covering benign activity and 14 attack categories.

The dataset is not included in this repository because of its size. Place the CICIDS2017 CSV files in a local data directory before running the notebook, then update the dataset path in the data-loading cell if necessary.

## Methodology

- Combined and cleaned CICIDS2017 network-flow CSV files
- Replaced infinite values and handled missing numerical data
- Created binary benign/attack labels while retaining multiclass attack labels
- Compared linear, ensemble, boosting, rule-based, and dummy baselines
- Tuned decision thresholds using validation data
- Evaluated precision, recall, F1, balanced accuracy, and confusion matrices
- Used cross-validation and source-file holdout testing
- Applied permutation importance and SHAP for model explainability
- Explored multiclass attack classification and class-level performance

## Tech Stack

Python, pandas, NumPy, scikit-learn, Matplotlib, Seaborn, SHAP, and Jupyter Notebook.

## Repository Structure

```text
.
|-- Summer BSP (Declaration + Code + Presentation)/
|   |-- Summer_BSP.ipynb
|   |-- Summer BSP Declaration.pdf
|   `-- Summer BSP Presentation.pdf
|-- Summer BSP Report.pdf
|-- Summer BSP Secondary Language Report.pdf
|-- .gitignore
|-- README.md
`-- requirements.txt
```

## Run Locally

```bash
git clone https://github.com/joburn-git/ml-network-intrusion-detection.git
cd ml-network-intrusion-detection

python -m venv .venv
source .venv/Scripts/activate
python -m pip install --upgrade pip
pip install -r requirements.txt
jupyter notebook "Summer BSP (Declaration + Code + Presentation)/Summer_BSP.ipynb"
```

## Limitations

- Random train/test splits can overestimate performance when related traffic appears across both sets.
- Source-file holdout testing showed reduced recall under distribution shift.
- The multiclass experiment was affected by severe imbalance among attack categories.
- CICIDS2017 represents a controlled environment and does not capture every production network condition.

