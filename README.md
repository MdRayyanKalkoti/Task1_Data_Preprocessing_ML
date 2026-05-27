# Task1_Data_Preprocessing

<div align="center">

![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-2.x-150458?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-1.x-013243?style=for-the-badge&logo=numpy&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-1.x-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![VS Code](https://img.shields.io/badge/VS%20Code-IDE-007ACC?style=for-the-badge&logo=visual-studio-code&logoColor=white)
![Kaggle](https://img.shields.io/badge/Kaggle-API-20BEFF?style=for-the-badge&logo=kaggle&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

**Machine Learning Internship — Task 1**
**TechnoHacks Solutions**

*A structured data preprocessing pipeline applied to the Student Performance Prediction dataset, covering null handling, categorical encoding, and feature normalization.*

</div>

---

## Overview

This project is **Task 1** of the Machine Learning Internship at **TechnoHacks Solutions**. The objective is to build a clean, reproducible data preprocessing pipeline as a foundational step before any machine learning model is trained.

Raw datasets rarely arrive in a model-ready format. This notebook systematically addresses that gap — inspecting data quality, resolving missing values, transforming categorical variables into numerical representations, and normalizing feature scales — ultimately producing a clean dataset ready for downstream ML workflows.

The entire pipeline is implemented in a single, well-documented Jupyter Notebook and version-controlled via Git and GitHub.

---

## Key Highlights

- Dataset sourced directly via the **Kaggle API** without manual downloads
- Comprehensive **exploratory data inspection** before any transformation
- **Label Encoding** applied to categorical columns for numerical compatibility
- **StandardScaler** normalization to bring all features onto a common scale
- Clean, processed dataset exported to the `outputs/` directory as a `.csv` file
- Fully reproducible workflow using a `requirements.txt` and structured project layout

---

## Tech Stack

| Tool / Library | Purpose |
|---|---|
| **Python 3.10+** | Core programming language |
| **Pandas** | Data loading, inspection, and transformation |
| **NumPy** | Numerical operations and array handling |
| **Scikit-learn** | Label encoding and StandardScaler normalization |
| **Jupyter Notebook** | Interactive, step-by-step preprocessing workflow |
| **Kaggle API** | Programmatic dataset download via terminal |
| **VS Code** | Primary development environment |
| **Git & GitHub** | Version control and project hosting |

---

## Project Structure

```
Task1_Data_Preprocessing/
│
├── datasets/                         # Raw dataset downloaded via Kaggle API
│
├── outputs/
│   └── cleaned_data.csv              # Final preprocessed and normalized dataset
│
├── Task1_Data_Preprocessing.ipynb    # Main Jupyter Notebook (full pipeline)
├── requirements.txt                  # Python dependencies
├── LICENSE                           # MIT License
└── README.md                         # Project documentation
```

---

## Dataset

**Name:** Student Performance Prediction Dataset
**Source:** [Kaggle](https://www.kaggle.com/)
**Access Method:** Kaggle API (see setup instructions below)

The dataset contains demographic, academic, and behavioral attributes of students. It is used here purely as a preprocessing exercise — the goal is to produce a clean, normalized version of the data rather than train a predictive model.

---

## Preprocessing Workflow

The notebook follows a linear, documented pipeline across the following stages:

**Step 1 — Dataset Acquisition**
The dataset is downloaded directly inside the VS Code terminal using the Kaggle API CLI, avoiding any manual browser downloads. The raw file is saved to the `datasets/` directory.

```bash
kaggle datasets download -d <dataset-identifier> -p datasets/ --unzip
```

**Step 2 — Data Loading**
The dataset is loaded into a Pandas DataFrame, followed by an initial inspection using `.shape`, `.head()`, `.info()`, and `.dtypes` to understand its dimensions, column types, and memory usage.

**Step 3 — Exploratory Data Quality Check**
Missing values are identified using `.isnull().sum()` and `.describe()` is used to profile numerical distributions. This step informs all subsequent transformation decisions.

**Step 4 — Handling Missing Values**
Null entries are handled through appropriate strategies — numerical columns are imputed using mean/median values, while categorical columns use mode imputation — ensuring no data is lost unnecessarily.

**Step 5 — Categorical Encoding**
Categorical string columns are converted into integer-encoded representations using `sklearn.preprocessing.LabelEncoder`. This makes the dataset compatible with numerical ML algorithms.

```python
from sklearn.preprocessing import LabelEncoder
le = LabelEncoder()
df['column_name'] = le.fit_transform(df['column_name'])
```

**Step 6 — Feature Normalization**
All numerical features are standardized using `sklearn.preprocessing.StandardScaler`, transforming each column to have a mean of 0 and a standard deviation of 1. This prevents high-magnitude features from dominating distance-based algorithms.

```python
from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()
df[numerical_cols] = scaler.fit_transform(df[numerical_cols])
```

**Step 7 — Cleaned Dataset Export**
The final preprocessed DataFrame is saved to `outputs/cleaned_data.csv` using `df.to_csv()`, ready for use in any subsequent modeling task.

---

## Getting Started

### Prerequisites

- Python 3.10 or higher
- A Kaggle account with an API token (`kaggle.json`)
- VS Code (recommended) or any Jupyter-compatible environment

### Installation

**1. Clone the repository**

```bash
git clone https://github.com/<your-username>/Task1_Data_Preprocessing.git
cd Task1_Data_Preprocessing
```

**2. Create and activate a virtual environment** *(optional but recommended)*

```bash
python -m venv venv
# Windows
venv\Scripts\activate
# macOS/Linux
source venv/bin/activate
```

**3. Install dependencies**

```bash
pip install -r requirements.txt
```

**4. Configure the Kaggle API**

Place your `kaggle.json` token file in the appropriate directory:

```bash
# macOS/Linux
~/.kaggle/kaggle.json

# Windows
C:\Users\<YourUsername>\.kaggle\kaggle.json
```

Ensure the file has the correct permissions (Linux/macOS):

```bash
chmod 600 ~/.kaggle/kaggle.json
```

**5. Download the dataset**

```bash
kaggle datasets download -d <dataset-identifier> -p datasets/ --unzip
```

**6. Open and run the notebook**

```bash
jupyter notebook Task1_Data_Preprocessing.ipynb
```

Or open the project folder directly in VS Code and run cells using the Jupyter extension.

---

## requirements.txt

```
pandas
numpy
scikit-learn
jupyter
kaggle
```

---

## Git & GitHub Workflow

This project was developed using a structured version control approach:

```bash
git init
git add .
git commit -m "Initial commit: data preprocessing pipeline"
git branch -M main
git remote add origin https://github.com/<your-username>/Task1_Data_Preprocessing.git
git push -u origin main
```

Changes at each preprocessing stage were committed incrementally to maintain a clean, readable project history.

---

## Output

After running the full notebook, the following file is generated:

| File | Location | Description |
|---|---|---|
| `cleaned_data.csv` | `outputs/` | Fully preprocessed, encoded, and normalized dataset |

---

## Internship Context

| Field | Details |
|---|---|
| **Organization** | TechnoHacks Solutions |
| **Role** | Machine Learning Intern |
| **Task** | Task 1 — Data Preprocessing |
| **Author** | Mohammad Rayyan Kalkoti |

---

## License

This project is licensed under the [MIT License](LICENSE).

```
MIT License

Copyright (c) 2024 Mohammad Rayyan Kalkoti

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
```

---

<div align="center">

*Developed as part of the Machine Learning Internship at TechnoHacks Solutions*
**Mohammad Rayyan Kalkoti**

## 📈 Future Improvements

- Advanced preprocessing techniques
- Automated preprocessing pipeline
- Machine learning model integration

</div>