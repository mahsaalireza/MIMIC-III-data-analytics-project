# Predicting Length of Stay for Post-Cardiac Surgery Patients with Diabetes (MIMIC-III)

_Data Analytics in Healthcare & Connected Care — MACS (Year 1)_  
**Team:** Jishya Keerthika Basisetty, Mahsa Alirezaee, Andre Vital, Tanjil Hasan — **Academic Year:** 2021/2022

This repository contains:
- **`MIMIC_III.ipynb`** — the end-to-end notebook for feature engineering and model training.
- **`DataAnalyticsFinalReport (1).pdf`** — the written report with data extraction details and results.

> Goal: classify **length of stay (LOS)** for diabetic patients undergoing **cardiac surgery** as **short (≤ 5 days)** or **long (> 5 days)** using **MIMIC-III**.

## 📦 Environment

Python **3.9+**. Install dependencies:

```bash
pip install -r requirements.txt
```

_Minimal stack (if you skip optional parts):_

```bash
pip install numpy pandas scikit-learn matplotlib seaborn
```

## 🗂️ Data Access (MIMIC-III)

Access to **MIMIC-III** requires credentialing and a data use agreement. Do **not** commit raw data or patient-level extracts. Configure your local credentials and point the notebook to your secure data source.

## 🧮 Methods (high level)

- **Data extraction & integration:** Core MIMIC-III tables (ADMISSIONS, PATIENTS, ICUSTAYS, DIAGNOSES_ICD, PROCEDURES_ICD, SERVICES, CPT) were joined to build a cohort focused on diabetes (ICD-9 25000) and post-cardiac-surgery cases.
- **Target definition:** LOS derived from `ADMITTIME`→`DISCHTIME`, binarized at 5 days.
- **Cleaning / feature engineering:** Removed inconsistent records (e.g., negative LOS, implausible ages), resolved missingness, encoded categoricals.
- **Models evaluated:** Decision Tree, Naïve Bayes, K-Nearest Neighbors (KNN), Support Vector Classifier (SVC), Ensembles: Voting, Bagging, AdaBoost, Random Forest.
- **Evaluation:** Train/test split; metrics include accuracy, precision, recall, F1; confusion matrices.

## 📊 Reported Results

| Model | Accuracy |
|---|---:|
| Decision Tree | 0.9041 |
| Naïve Bayes | 0.5205 |
| KNN | 0.9236 |
| SVC | 0.5885 |
| Voting Classifier | 0.7585 |
| Random Forest | 0.8844 |
| KNN (after hyperparameter tuning) | 0.9308 |

Best reported: **KNN after hyperparameter tuning** with **0.9308** accuracy on the test set.

## ▶️ How to Run

1. Create and activate a virtual environment.
2. `pip install -r requirements.txt`
3. Configure access to MIMIC-III (database or CSV extracts). Update paths/connection strings in **`MIMIC_III.ipynb`** if needed.
4. Launch Jupyter and execute the notebook top-to-bottom:
   ```bash
   jupyter lab  # or jupyter notebook
   ```

## 🔐 Compliance & Ethics

- **PHI:** Never commit Protected Health Information.
- **Reproducibility:** Set random seeds and record package versions; clear outputs and re-run before pushing.
- **Data sharing:** Share only aggregate results and code; keep data access behind institutional controls.

## 📁 Repository Structure

```
.
├── MIMIC_III.ipynb
├── DataAnalyticsFinalReport (1).pdf
├── README.md
└── requirements.txt
```

## 🙏 Acknowledgements

- MIMIC-III creators and maintainers.
- scikit-learn, NumPy, Pandas, Matplotlib, Seaborn.
- Project contributors: Jishya Keerthika Basisetty, Mahsa Alirezaee, Andre Vital, Tanjil Hasan.
