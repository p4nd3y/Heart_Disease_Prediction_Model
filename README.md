# 🫀 Heart Disease & Cardiovascular Risk Prediction Pipeline

An end-to-end data analysis and machine learning preparation repository for predicting cardiovascular disease risk using demographic, electrocardiographic, and clinical health indicators from the `heart.csv` dataset.

---

## 📁 Repository Contents

| File | Description |
| :--- | :--- |
| **[`heart.csv`](./heart.csv)** | Cardiovascular health dataset containing 918 patient observations and 11 clinical features + 1 target variable. |
| **[`ML01(heart).ipynb`](./ML01(heart).ipynb)** | Interactive Jupyter Notebook containing Exploratory Data Analysis (EDA), univariate/bivariate visual analytics, distribution analysis, categorical encoding, and feature standardization. |
| **[`README.md`](./README.md)** | Project documentation, comprehensive dataset dictionary, clinical insights, and pipeline workflow. |

---

## 📊 Dataset Dictionary & Clinical Attributes

The dataset combines multiple cardiovascular diagnostic records into **918 patient samples**:

| Feature Name | Type | Description | Values / Units |
| :--- | :--- | :--- | :--- |
| `Age` | Integer | Patient age in years | 28 – 77 years |
| `Sex` | Categorical | Biological sex | `M` (Male), `F` (Female) |
| `ChestPainType` | Categorical | Type of chest pain reported | `TA` (Typical Angina)<br>`ATA` (Atypical Angina)<br>`NAP` (Non-Anginal Pain)<br>`ASY` (Asymptomatic) |
| `RestingBP` | Integer | Resting blood pressure | mm Hg (e.g., 80 – 200) |
| `Cholesterol` | Integer | Serum cholesterol level | mg/dL (e.g., 0 – 603) |
| `FastingBS` | Binary | Fasting blood sugar level | `1`: FastingBS > 120 mg/dL<br>`0`: FastingBS ≤ 120 mg/dL |
| `RestingECG` | Categorical | Resting electrocardiographic results | `Normal`: Normal<br>`ST`: ST-T wave abnormality<br>`LVH`: Left ventricular hypertrophy |
| `MaxHR` | Integer | Maximum heart rate achieved during stress test | 60 – 202 bpm |
| `ExerciseAngina` | Binary / Cat | Exercise-induced angina | `Y` (Yes), `N` (No) |
| `Oldpeak` | Float | ST depression induced by exercise relative to rest | -2.6 to 6.2 |
| `ST_Slope` | Categorical | Slope of peak exercise ST segment | `Up` (Upsloping)<br>`Flat` (Flat)<br>`Down` (Downsloping) |
| `HeartDisease` | Binary (**Target**) | Presence of heart disease | `1`: Heart Disease diagnosed<br>`0`: Normal / No Heart Disease |

---

## 🔬 Exploratory Data Analysis & Clinical Insights

### 1. Key Diagnostic Indicators
* **Chest Pain Presentation**: Patients presenting with **Asymptomatic (`ASY`)** chest pain have significantly higher rates of diagnosed heart disease compared to those presenting with Typical Angina (`TA`) or Atypical Angina (`ATA`).
* **Exercise Angina & ST Slope**:
  * An exercise ST slope that is **`Flat`** or **`Downsloping`** is strongly associated with ischemic cardiac events.
  * Presence of **Exercise-Induced Angina (`ExerciseAngina = Y`)** strongly increases the probability of cardiovascular disease.
* **Max Heart Rate (`MaxHR`) vs Age**: Older individuals show reduced cardiovascular exercise tolerance and lower maximum heart rates. Patients with heart disease systematically achieve lower `MaxHR` values during stress evaluations.

### 2. Visualizations in the Notebook
* **Count Plots**: Distribution of `HeartDisease` conditioned on `Sex`, `ChestPainType`, `FastingBS`, `ExerciseAngina`, and `ST_Slope`.
* **Distribution & Outlier Boxplots**: Age, Cholesterol, RestingBP, and Oldpeak distributions segmented by cardiac outcome.
* **Violin & Kernel Density Plots**: Multi-modal age and cholesterol density comparisons.
* **Correlation Heatmaps**: Pairwise numerical correlation matrix identifying strongest linear relationships with the target variable.

---

## 🛠️ Data Preprocessing & Pipeline Steps

1. **Handling Missing Values & Outlier Diagnostics**:
   * Evaluates zero-value artifacts in `Cholesterol` and `RestingBP`.
2. **Categorical Feature Encoding**:
   * One-hot encoding applied via `pd.get_dummies(..., drop_first=True)` to convert multi-class categories (`ChestPainType`, `RestingECG`, `ST_Slope`, `Sex`, `ExerciseAngina`) into binary numeric features.
3. **Feature Scaling**:
   * Standardizes continuous variables (`Age`, `RestingBP`, `Cholesterol`, `MaxHR`, `Oldpeak`) using `StandardScaler` ($\mu = 0, \sigma = 1$) to prepare features for distance- and gradient-based classification algorithms (e.g., Logistic Regression, SVM, KNN, Neural Networks).

---

## 🚀 Getting Started

### Prerequisites

Install the necessary scientific Python packages:

```bash
pip install numpy pandas scikit-learn matplotlib seaborn jupyter
```

### Running the Notebook

1. Clone the repository:
   ```bash
   git clone https://github.com/p4nd3y/Heart_Model_Data.git
   cd Heart_Model_Data
   ```

2. Open the notebook with Jupyter:
   ```bash
   jupyter notebook "ML01(heart).ipynb"
   ```

3. Execute cells sequentially to inspect the dataset, reproduce the charts, and inspect the preprocessed feature vectors.

---

## 📄 License
This repository is open for research, academic, and portfolio usage.
