# Intelligent Network Intrusion Detection Using Machine Learning, Neural Networks, and Explainable AI

## Project Overview

Enterprise networks generate large volumes of traffic every day from users, applications, cloud services, endpoints, and connected systems. As network activity increases, cybersecurity teams must identify malicious behavior hidden within normal traffic patterns. Traditional security tools such as firewalls, signature-based intrusion detection systems, and rule-based alerts are important, but they may struggle to detect unusual, evolving, or previously unseen attack patterns.

This project develops a proof-of-concept network intrusion detection system using traditional machine learning, neural network models, anomaly detection, and explainability techniques. The project uses the CICIDS2017 dataset to classify network traffic as benign or malicious and to evaluate whether specific attack categories can be identified from network flow features.

The project is designed as a capstone-level applied AI workflow. It includes data ingestion, data cleaning, exploratory data analysis, feature preparation, class imbalance handling, traditional machine learning models, neural network training, autoencoder-based anomaly detection, model evaluation, error analysis, and feature-level explainability.

## Project Objectives

The primary objectives of this project are to:

- Build a machine learning workflow for network intrusion detection using CICIDS2017.
- Classify network traffic as benign or malicious using network flow features.
- Compare traditional machine learning models with neural network-based models.
- Evaluate whether neural network models provide meaningful improvement over traditional models.
- Analyze model performance using cybersecurity-relevant metrics.
- Examine false positives and false negatives from a Security Operations Center perspective.
- Use feature-level analysis or explainability methods to understand important traffic characteristics.
- Produce a reproducible project repository with clear documentation and execution steps.

## Research Question

Can machine learning and neural network models learn useful patterns from network flow data to accurately detect malicious network activity and support cybersecurity analyst decision-making?

## High-Level Hypothesis

Machine learning models can learn meaningful patterns from CICIDS2017 network flow features and classify malicious activity effectively. However, traditional models such as Random Forest or XGBoost may provide performance comparable to neural network models while offering better interpretability and lower computational cost.

## Dataset

This project uses the CICIDS2017 dataset from the Canadian Institute for Cybersecurity at the University of New Brunswick.

Dataset source:

https://www.unb.ca/cic/datasets/ids-2017.html

The dataset contains labeled network traffic records generated from benign activity and multiple attack scenarios. The project uses the machine learning CSV files generated from CICFlowMeter rather than the raw PCAP files.

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

## Intended Users

The intended users of this proof-of-concept system are:

- Cybersecurity analysts
- Security Operations Center teams
- Network administrators
- Incident response teams
- Security engineering teams

The model is not intended to replace human analysts or existing security tools. Instead, it is designed as a decision-support capability that can help identify suspicious traffic patterns, prioritize alerts, and support faster investigation.

## Project Scope

This project includes:

- Data ingestion and dataset inventory
- Data cleaning and preprocessing
- Exploratory data analysis
- Missing value, duplicate, infinite value, and outlier review
- Class imbalance analysis
- Data leakage review
- Feature preparation and scaling
- Binary intrusion detection
- Multiclass attack classification
- Traditional machine learning model training
- Neural network model training
- Autoencoder-based anomaly detection
- Hyperparameter tuning
- Model comparison
- Error analysis
- Explainability or feature importance analysis
- Final report, presentation, and reproducible GitHub repository

## Models

The project will compare multiple modeling approaches.

### Traditional Machine Learning Models

- Logistic Regression
- Decision Tree
- Random Forest
- XGBoost or Gradient Boosting

### Neural Network and Deep Learning Models

- Multilayer Perceptron classifier
- Autoencoder-based anomaly detection

## Evaluation Metrics

The project will evaluate model performance using metrics that are important for intrusion detection:

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

Accuracy alone is not sufficient for intrusion detection because the dataset may be imbalanced and missed attacks can have a high operational cost. Special attention is placed on recall, false negatives, and the trade-off between detecting attacks and managing alert volume.

## Repository Structure

The repository is organized as follows:

```text
.
├── README.md
├── requirements.txt
├── data/
│   ├── raw/
│   ├── processed/
│   └── interim/
├── notebooks/
│   ├── 01_data_ingestion_and_validation.ipynb
│   ├── 02_data_cleaning_and_eda.ipynb
│   ├── 03_feature_engineering.ipynb
│   ├── 04_traditional_ml_models.ipynb
│   ├── 05_neural_network_models.ipynb
│   ├── 06_autoencoder_anomaly_detection.ipynb
│   └── 07_model_evaluation_and_explainability.ipynb
├── src/
│   ├── data/
│   ├── features/
│   ├── models/
│   ├── evaluation/
│   └── visualization/
├── models/
├── reports/
│   ├── figures/
│   └── tables/
└── docs/
```

The `data/` directory is not expected to contain the full CICIDS2017 dataset in GitHub because of file size. Users should download the dataset from the official source and place the CSV files in `data/raw/`.

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

If TensorFlow installation on Apple Silicon requires additional setup, use the Apple-compatible TensorFlow package or run the neural network notebooks in Google Colab.

## How to Run the Project

1. Download the CICIDS2017 machine learning CSV files from the official dataset page.
2. Place the CSV files in the `data/raw/` directory.
3. Run the notebooks in order:
   - `01_data_ingestion_and_validation.ipynb`
   - `02_data_cleaning_and_eda.ipynb`
   - `03_feature_engineering.ipynb`
   - `04_traditional_ml_models.ipynb`
   - `05_neural_network_models.ipynb`
   - `06_autoencoder_anomaly_detection.ipynb`
   - `07_model_evaluation_and_explainability.ipynb`
4. Review generated figures and tables in the `reports/` directory.
5. Review saved models in the `models/` directory.

## Expected Outputs

The project will produce:

- Cleaned and processed dataset files
- Exploratory data analysis charts
- Class distribution and imbalance analysis
- Trained traditional machine learning models
- Trained Multilayer Perceptron model
- Autoencoder anomaly detection results
- Model comparison tables
- Confusion matrices
- ROC and PR curves
- Feature importance or explainability outputs
- Final report and presentation materials

## Data Privacy and Ethics

The CICIDS2017 dataset is a public cybersecurity research dataset and does not contain private customer records or personally identifiable information for this academic use case. In a real production environment, network traffic logs could contain sensitive metadata, system identifiers, or user-related information. Therefore, a live implementation would require strong access controls, data minimization, retention controls, and governance review.

The model should also be used carefully because false positives can increase analyst workload, while false negatives can allow attacks to go undetected. The system is intended to support human decision-making, not replace analyst judgment.

## Limitations

This project is a proof of concept and does not represent a production-ready intrusion detection platform. Key limitations include:

- CICIDS2017 may not fully represent current enterprise network behavior.
- Model performance on the dataset may not directly transfer to live environments.
- Some attack classes may be imbalanced or underrepresented.
- Network traffic patterns can drift over time.
- Real deployment would require monitoring, retraining, and integration with security tools.

## Final Deliverables

The final capstone deliverables include:

- Formal project report
- GitHub repository with code and documentation
- Final presentation
- Trained models and evaluation artifacts
- Explainability and model comparison results

## References

Canadian Institute for Cybersecurity. (n.d.). *Intrusion detection evaluation dataset (CICIDS2017).* University of New Brunswick. Retrieved July 5, 2026, from https://www.unb.ca/cic/datasets/ids-2017.html


## Author

Ajay Kamble

Master of Science in Applied Artificial Intelligence  
University of San Diego
