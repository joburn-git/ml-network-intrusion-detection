# Machine Learning-Based Network Intrusion Detection System

**Author:** João Bernardo Sousa Faria

This project builds a machine learning prototype for detecting malicious network traffic using the CICIDS2017 network-flow dataset. The work compares supervised learning models against simple baselines, evaluates class imbalance effects, and uses explainability methods to understand which network-flow features influence intrusion detection decisions.

## Highlights

- Built a binary intrusion detector for BENIGN vs ATTACK network flows.
- Compared Logistic Regression, Random Forest, tuned Random Forest, HistGradientBoosting, a rule-based baseline, and a dummy majority baseline.
- Evaluated model performance with precision, recall, F1-score, balanced accuracy, confusion matrices, cross-validation, threshold tuning, and source-file holdout testing.
- Used SHAP and permutation importance to interpret the strongest model.
- Extended the analysis to multiclass attack classification to study the difficulty of identifying specific attack categories.

## Results

The strongest binary model was **HistGradientBoosting**, achieving an attack F1-score of **0.9953** on the random test split with attack recall of **0.9957**. Three-fold cross-validation confirmed stable performance, with mean attack F1-score of **0.9917**.

A stricter source-file holdout evaluation reduced attack F1-score to **0.7551**, showing that random train-test splits can overestimate intrusion detection performance. This makes the project more realistic and professionally useful because it discusses both strong results and generalization limits.

## Tech Stack

- Python
- pandas and NumPy
- scikit-learn
- SHAP
- matplotlib and seaborn
- Jupyter Notebook

## Repository Structure

```text
.
|-- notebooks/
|   `-- network_intrusion_detection_cicids2017.ipynb
|-- README.md
|-- requirements.txt
`-- .gitignore
```

## How To Run

From Git Bash:

```bash
python -m venv .venv
source .venv/Scripts/activate
pip install -r requirements.txt
jupyter lab notebooks/network_intrusion_detection_cicids2017.ipynb
```

The notebook downloads or locates the CICIDS2017 CSV files locally. The dataset is not committed to the repository because of size and reproducibility concerns.

## Project Notes

This is an academic portfolio project focused on machine learning for cybersecurity. The main objective is not only to maximize a metric, but also to evaluate whether model performance remains credible under more realistic testing conditions.
