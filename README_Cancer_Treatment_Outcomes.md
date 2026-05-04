# 🎗️ Cancer Treatment Outcomes Prediction

![Python](https://img.shields.io/badge/Python-3.10-blue)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-ML-orange)
![Domain](https://img.shields.io/badge/Domain-Oncology%20%2F%20Healthcare-red)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![Course](https://img.shields.io/badge/Course-Data%20Science%20Final%20Project-purple)

---

## 📌 Project Overview

This project predicts **whether a cancer patient will survive 6 months** based on their cancer type, stage, tumor characteristics, treatment plan, and clinical biomarkers.

Early survival prediction allows oncologists to:
- Customize treatment intensity for high-risk patients
- Initiate palliative care planning proactively
- Allocate hospital resources more effectively
- Improve patient counseling and family communication

---

## 🏥 Dataset Description

**File:** `cancer_treatment_outcomes.csv`  
**Records:** 100 patients  
**Features:** 24 clinical + treatment columns  
**Target:** `Survival_6Months` (1 = Survived, 0 = Did Not Survive)

### Cancer Types Covered
| Cancer Type | Gender Focus | Key Biomarker |
|---|---|---|
| Breast | Female | CA125 |
| Lung | Male/Female | WBC Count |
| Prostate | Male | PSA Level |
| Ovarian | Female | CA125 |
| Colorectal | Male/Female | Hemoglobin |
| Cervical | Female | CA125 |

### Cancer Stages
- **Stage I** — Localized, small tumor, no spread
- **Stage II** — Locally advanced
- **Stage III** — Lymph node involvement
- **Stage IV** — Metastatic, most severe

### Treatment Types
- Surgery, Chemotherapy, Radiation, Combined, Surgery+Chemo, Palliative

---

## 📋 Column Reference

| Column | Type | Description |
|---|---|---|
| Age | Numeric | Patient age in years |
| Gender | Categorical | Male / Female |
| Cancer_Type | Categorical | Type of cancer |
| Cancer_Stage | Ordinal | I → IV |
| Tumor_Size_cm | Numeric | Tumor size in cm |
| Metastasis | Binary | Cancer spread: Yes/No |
| Treatment_Type | Categorical | Treatment approach |
| Treatment_Duration_Weeks | Numeric | Treatment length |
| Chemotherapy_Cycles | Numeric | Number of chemo cycles |
| Radiation_Sessions | Numeric | Radiation count |
| Surgery_Performed | Binary | Yes/No |
| Targeted_Therapy | Binary | Yes/No |
| Immunotherapy | Binary | Yes/No |
| WBC_Count | Numeric | White blood cell count (µL) |
| Hemoglobin | Numeric | Hemoglobin level (g/dL) |
| Platelet_Count | Numeric | Platelet count (µL) |
| CA125_Marker | Numeric | Ovarian/cancer marker (U/mL) |
| PSA_Level | Numeric | Prostate specific antigen (ng/mL) |
| Performance_Score | Numeric | Functional status 0–100 |
| Pain_Level | Numeric | Pain scale 1–10 |
| Weight_Loss_kg | Numeric | Weight lost during treatment (kg) |
| Hospital_Visits | Numeric | Total visits during treatment |
| Complication_Occurred | Binary | Major complication: Yes/No |
| **Survival_6Months** | **TARGET** | **1 = Survived, 0 = Did Not** |

---

## ⚙️ Feature Engineering

6 new features created to boost model performance:

| Feature | Logic | Clinical Relevance |
|---|---|---|
| `Severity_Score` | Stage×2 + Metastasis×3 + Complication | Overall disease burden |
| `Treatment_Intensity` | Weighted sum of all treatment types | Aggressiveness of care |
| `Is_Anemic` | Hemoglobin < 10 g/dL | Systemic weakness indicator |
| `High_Pain` | Pain Level ≥ 7 | Disease burden proxy |
| `Severe_Weight_Loss` | Weight Loss > 5 kg | Cachexia / malnutrition |
| `Elderly_Patient` | Age ≥ 70 | Age-related risk factor |

---

## 🤖 Models Used

| # | Model | Type | Notes |
|---|---|---|---|
| 1 | Logistic Regression | Linear | Baseline, uses scaled features |
| 2 | Decision Tree | Tree-based | Interpretable, depth=6 |
| 3 | Random Forest | Ensemble | 100 trees, strong performer |
| 4 | **Gradient Boosting** | **Ensemble** | **Best model — boosted trees** |

---

## 📊 Results Summary

| Model | Accuracy | AUC Score |
|---|---|---|
| Logistic Regression | ~85% | ~0.92 |
| Decision Tree | ~88% | ~0.94 |
| Random Forest | ~91% | ~0.97 |
| **Gradient Boosting** | **~93%** | **~0.98** |

**Winner: Gradient Boosting** — highest accuracy and AUC on test set.

---

## 🔍 Key Findings

1. **Cancer Stage** — most powerful predictor; Stage IV = ~5% survival rate
2. **Performance Score** — patients below 40 rarely survive 6 months
3. **Metastasis + Complication** — combination drastically reduces survival odds
4. **Hemoglobin** — anemic patients (< 10 g/dL) show significantly lower survival
5. **Weight Loss > 5 kg** — strong indicator of systemic disease progression
6. **Elderly patients (70+)** — higher vulnerability across all cancer types

---

## 🚀 How to Run

```bash
# 1. Clone the repository
git clone https://github.com/your-username/cancer-treatment-outcomes.git
cd cancer-treatment-outcomes

# 2. Install dependencies
pip install pandas numpy matplotlib seaborn scikit-learn jupyter

# 3. Launch Jupyter
jupyter notebook Cancer_Treatment_Outcomes.ipynb
```

Run all cells top to bottom — no external dependencies or API keys needed.

---

## 📁 Project Structure

```
cancer_project/
│
├── cancer_treatment_outcomes.csv    ← Unique hardcoded dataset (100 patients)
├── Cancer_Treatment_Outcomes.ipynb  ← Complete step-by-step Jupyter Notebook
├── Cancer_Treatment_Presentation.pptx ← 9-slide professional presentation
└── README.md                        ← This file
```

---

## 🛠️ Requirements

```
python >= 3.8
pandas
numpy
matplotlib
seaborn
scikit-learn
jupyter
```

---

## ⚠️ Disclaimer

This dataset is synthetically generated for educational purposes. It is inspired by real-world clinical patterns but does not represent real patient data. Do not use for actual clinical decision-making.

---

## 👨‍💻 Author

**[Your Name]**  
Data Science Course — Final Project  
Week 8 Submission

---

## 📄 License

Educational use only. Created as part of a Data Science course final project.
