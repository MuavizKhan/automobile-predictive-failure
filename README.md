# Automobile Predictive Failure Detection (AI4I 2020)

## Overview
This repository contains an end-to-end **predictive failure detection** pipeline using machine-learning models trained on the **AI4I 2020 Predictive Maintenance Dataset**. The objective is to predict whether a failure is likely to occur (**Target = 1**) or not (**Target = 0**) using sensor features such as temperature, rotational speed, torque, and tool wear.

The project is implemented primarily in a **Jupyter Notebook (`main_project.ipynb`)** and includes:
- dataset validation + cleanup
- detailed EDA (plots + correlation)
- outlier handling (IQR capping / winsorization)
- categorical encoding (`Type`)
- proper train/test split with `stratify`
- scaling (fit on train only)
- class imbalance handling (SMOTE on train only)
- training & comparison of multiple ML models
- hyperparameter tuning (RandomizedSearchCV for Random Forest)
- feature importance visualization
- saving deployment artifacts + inference helper

---

## Dataset
The dataset used is the **[AI4I 2020 Predictive Maintenance Dataset](https://archive.ics.uci.edu/dataset/601/ai4i+2020+predictive+maintenance+dataset)**.

### Columns (raw)
- **UDI**: Unique identifier *(dropped)*
- **Product ID**: Identifier of the manufactured product *(dropped)*
- **Type**: Product type (H/M/L)
- **Air temperature [K]**
- **Process temperature [K]**
- **Rotational speed [rpm]**
- **Torque [Nm]**
- **Tool wear [min]**
- **Target**: Failure label (0 = No Failure, 1 = Failure)

### Features used for modeling
After dropping `UDI` and `Product ID`, the model uses:
- `Type` (encoded)
- `Air temperature [K]`
- `Process temperature [K]`
- `Rotational speed [rpm]`
- `Torque [Nm]`
- `Tool wear [min]`

---

## Workflow Summary (What `main_project.ipynb` does)
### 1) Data Loading + Validation
- Loads CSV
- checks dataset is not empty
- confirms `Target` column exists

### 2) Exploratory Data Analysis (EDA)
Includes:
- target distribution (class imbalance)
- univariate histograms with KDE
- violin plots by target
- KDE plots split by target
- pairplot for interactions
- correlation heatmap

### 3) Outlier Handling (IQR Capping)
- uses IQR bounds
- **caps** extreme values instead of deleting rows (more stable, keeps data size)

### 4) Preprocessing
- encodes `Type`
- splits X/y
- train/test split with stratification
- standard scaling (fit on train only)

### 5) Class Imbalance Handling
- SMOTE is applied **only on training data**
- test set remains untouched (industry-correct evaluation)

### 6) Model Benchmarking
Trains and compares:
- Logistic Regression
- KNN
- SVC
- Random Forest
- Naive Bayes
- Decision Tree
- MLP Neural Network

Metrics computed:
- Accuracy
- Precision
- Recall
- F1 Score
- ROC-AUC (when available)
- Confusion matrix plots for each model
- Bar chart comparing metrics across models

### 7) Hyperparameter Tuning
- RandomizedSearchCV on Random Forest (scoring = F1)
- evaluation of tuned model on test set

### 8) Feature Importance
- Random Forest feature importances plotted + saved for interpretation

### 9) Deployment Artifacts + Inference
Saves artifacts to `artifacts/`:
- `best_rf_model.joblib`
- `standard_scaler.joblib`
- `metadata.json`
- `type_encoder.joblib` *(if used)*

Also includes a helper function for predicting failure risk on a new sample.

---

## Example Outputs

### Target Distribution
<img width="484" height="384" alt="image" src="https://github.com/user-attachments/assets/fc77b1b7-f2e5-4b8d-ac58-00a563e085ec" />


### Correlation Matrix
<img width="861" height="584" alt="image" src="https://github.com/user-attachments/assets/31435acb-a118-453e-b3e8-0c0df7b13b7b" />


### Feature importance (best model)
<img width="884" height="484" alt="image" src="https://github.com/user-attachments/assets/456053c9-1c73-44d6-896b-fed4265f01ca" />


### Precision-Recall Curve (RF)
<img width="584" height="384" alt="image" src="https://github.com/user-attachments/assets/59e02004-c3b8-4eff-a37a-65ce340b618b" />


### Performance Comparison
<img width="1185" height="584" alt="image" src="https://github.com/user-attachments/assets/fd0cf828-2bef-4b58-bb02-27a638438302" />


---

## How to Run

### Option A — Run in Google Colab
1. Open `main_project.ipynb` in Colab.
2. Upload the dataset file (or keep it in the notebook directory).
3. Run all cells top-to-bottom.

### Option B — Run in VS Code (Local)
1. Clone this repository:
```bash
git clone https://github.com/MuavizKhan/automobile-predictive-failure.git
cd automobile-predictive-failure
