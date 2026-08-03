# Intelligent Network Intrusion Detection Using Machine Learning, Neural Networks, and Explainable AI

## Project Overview

This project develops a proof-of-concept network intrusion detection system using traditional machine learning, deep learning, anomaly detection, hybrid modeling, and explainability techniques. The system uses CICIDS2017 network-flow data to classify traffic as benign or malicious and to evaluate whether network-flow features can support cybersecurity analyst decision-making.

The final implementation is contained in one end-to-end notebook. The workflow includes data loading, data cleaning, exploratory data analysis, feature preparation, train/validation/test splitting, supervised model training, neural-network training, autoencoder-based anomaly detection, hybrid model evaluation, SHAP explainability, inference, drift monitoring logic, retraining workflow demonstration, and model artifact saving.

## Project Objectives

The primary objectives of this project are to:

- Build an end-to-end machine learning workflow for network intrusion detection.
- Classify network traffic as benign or malicious using CICIDS2017 network-flow features.
- Compare traditional machine learning models with neural-network-based models.
- Evaluate a hybrid XGBoost and neural-network model.
- Use cybersecurity-relevant metrics such as recall, F1-score, ROC-AUC, PR-AUC, false positive rate, and false negative rate.
- Analyze false positives and false negatives from a Security Operations Center perspective.
- Use SHAP and feature-importance analysis to explain model behavior.
- Demonstrate inference, monitoring logic, retraining workflow, and model versioning artifacts.

## Research Question

Can machine learning and neural-network models learn useful patterns from network-flow data to accurately detect malicious network activity and support cybersecurity analyst decision-making?

## High-Level Hypothesis

Machine learning models can learn meaningful patterns from CICIDS2017 network-flow features and classify malicious traffic effectively. Traditional models such as XGBoost may perform strongly on structured tabular network-flow data, while neural-network and hybrid approaches may provide additional value for nonlinear pattern learning and lifecycle-ready detection.

## Dataset

This project uses the CICIDS2017 dataset from the Canadian Institute for Cybersecurity at the University of New Brunswick.

Dataset source:

https://www.unb.ca/cic/datasets/ids-2017.html

The project uses the MachineLearningCSV files generated from CICFlowMeter, not the raw PCAP files.

Example traffic categories include:

- Benign traffic
- DoS attacks
- DDoS attacks
- PortScan
- Botnet traffic
- Brute Force attacks
- Web attacks
- Infiltration
- Heartbleed

### Dataset Not Included in GitHub

The full CICIDS2017 dataset is not included in this repository because of file size. To run the notebook, download the MachineLearningCSV files from the official dataset source and place the CSV files in:

```text
data/raw/
```

The repository includes placeholder folders only. Large raw, interim, processed, and model artifact files should remain outside Git tracking.

## Intended Users

The intended users of this proof-of-concept system are:

- Cybersecurity analysts
- Security Operations Center teams
- Network administrators
- Incident response teams
- Security engineering teams

The model is not intended to replace human analysts or existing security tools. It is designed as a decision-support capability that can help identify suspicious traffic patterns, prioritize alerts, and support investigation.

## Project Scope

This project includes:

- Dataset inventory and loading
- Data cleaning and preprocessing
- Exploratory data analysis
- Missing value, duplicate, infinite value, and outlier review
- Class imbalance analysis
- Data leakage review
- Feature engineering and scaling
- Stratified train/validation/test split
- Binary intrusion detection
- Traditional machine learning model training
- Neural-network classifier training
- Autoencoder-based anomaly detection
- Hybrid XGBoost and neural-network model
- Hyperparameter tuning and threshold selection
- Model comparison and error analysis
- SHAP explainability and feature-importance analysis
- Batch and single-record inference
- Drift monitoring logic
- Retraining workflow demonstration
- Model artifact saving and versioning metadata

## Models

The project compares the following approaches.

### Traditional Machine Learning Models

- Logistic Regression
- K-Nearest Neighbors
- Decision Tree
- Random Forest
- Gradient Boosting
- XGBoost

### Deep Learning and Hybrid Models

- Multilayer Perceptron neural-network classifier
- Autoencoder-based anomaly detection model
- Hybrid XGBoost and neural-network model

## Evaluation Metrics

The project evaluates model performance using intrusion-detection-relevant metrics:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- PR-AUC
- False positive rate
- False negative rate
- Confusion matrix
- Classification report

Accuracy alone is not sufficient for intrusion detection because the dataset is imbalanced and missed attacks can have high operational cost. This project emphasizes recall, false negatives, precision, and alert-quality trade-offs.

## Repository Structure

The repository is organized around one final notebook:

```text
.
├── README.md
├── requirements.txt
├── .gitignore
├── data/
│   ├── raw/                  # Place downloaded CICIDS2017 CSV files here
│   ├── interim/              # Optional intermediate files, not tracked
│   └── processed/            # Optional processed files, not tracked
├── notebooks/
│   └── aai590_cicids_final_submission_xgboost_nn_hybrid_shap_professional.ipynb
├── src/
│   └── __init__.py           # Placeholder for reusable source code
├── models/                   # Saved model artifacts, not tracked
├── reports/
│   ├── figures/              # Generated plots and report figures
│   └── tables/               # Generated result tables
└── docs/                     # Final report and presentation files
```

### Notes on Folder Usage

- `notebooks/` contains the single end-to-end final notebook.
- `data/raw/` is where users should place the downloaded CICIDS2017 MachineLearningCSV files.
- `data/`, `models/`, and large generated artifacts should not be committed to GitHub.
- `reports/figures/` and `reports/tables/` may contain selected final outputs used in the report.
- `src/` is included only as a placeholder for future modularization because this submission uses one notebook.

## Recommended `.gitignore`

Use the following rules to avoid committing large datasets and model artifacts:

```gitignore
# Python
__pycache__/
*.py[cod]
.ipynb_checkpoints/
.venv/
venv/
env/

# Data files
data/raw/*
data/interim/*
data/processed/*
!data/raw/.gitkeep
!data/interim/.gitkeep
!data/processed/.gitkeep

# Model artifacts
models/*
!models/.gitkeep
*.pkl
*.joblib
*.h5
*.keras
*.onnx

# Generated outputs
reports/figures/*
reports/tables/*
!reports/figures/.gitkeep
!reports/tables/.gitkeep

# System files
.DS_Store
Thumbs.db
```

## Environment Setup

Create a Python virtual environment:

```bash
python -m venv .venv
```

Activate the environment on macOS or Linux:

```bash
source .venv/bin/activate
```

Activate the environment on Windows:

```bash
.venv\Scripts\activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

## Suggested Requirements

The project may use the following core libraries:

```text
pandas
numpy
scikit-learn
matplotlib
seaborn
xgboost
tensorflow
keras
shap
joblib
jupyter
```

On Apple Silicon, TensorFlow may require additional setup. If local installation is difficult, run the notebook in Google Colab or another managed Python environment.

## How to Run the Project

1. Download the CICIDS2017 MachineLearningCSV files from the official dataset page.
2. Place all CSV files in the `data/raw/` directory.
3. Install the required Python packages.
4. Open the final notebook:

```text
notebooks/aai590_IDS.ipynb
```

5. Run the notebook from top to bottom.
6. Review generated model results, plots, SHAP outputs, inference outputs, monitoring outputs, and saved artifacts.

## Expected Outputs

The notebook produces:

- Dataset inventory and validation summaries
- Cleaned modeling dataset
- Exploratory data analysis charts
- Class distribution and imbalance analysis
- Train/validation/test split summary
- Traditional machine learning model results
- Neural-network training history
- Autoencoder anomaly detection results
- Hybrid model results
- Confusion matrices
- ROC and precision-recall curves
- SHAP feature-importance outputs
- Inference demonstration
- Drift monitoring output
- Retraining workflow demonstration
- Saved model artifacts and metadata

## Data Privacy and Ethics

CICIDS2017 is a public cybersecurity research dataset and does not contain private customer records for this academic use case. In a real production environment, network logs may contain sensitive metadata, system identifiers, IP-related information, or user-related activity. A production implementation would require access controls, data minimization, retention limits, monitoring governance, and security review.

The model should be used as a decision-support tool. False positives can increase analyst workload, while false negatives can allow attacks to remain undetected. Analyst review is required before taking operational action.

## Limitations

This project is a proof of concept and does not represent a production-ready intrusion detection platform. Key limitations include:

- CICIDS2017 may not fully represent current enterprise network behavior.
- Model performance on CICIDS2017 may not directly transfer to live environments.
- Some attack types are rare or underrepresented.
- Network traffic patterns can drift over time.
- Monitoring and retraining were demonstrated in the notebook, not deployed as a live automated production pipeline.
- Real deployment would require integration with security tools, alert workflows, governance, and continuous monitoring.

## Final Deliverables

The final capstone deliverables include:

- Formal project report
- GitHub repository with code and documentation
- Final presentation
- Final notebook
- Model evaluation artifacts
- Explainability and model comparison results

## References

Canadian Institute for Cybersecurity. (n.d.). *Intrusion detection evaluation dataset (CICIDS2017).* University of New Brunswick. Retrieved July 5, 2026, from https://www.unb.ca/cic/datasets/ids-2017.html

## Author

Ajay Kamble

Master of Science in Applied Artificial Intelligence  
University of San Diego
