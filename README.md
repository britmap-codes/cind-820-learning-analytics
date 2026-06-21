# cind-820-learning-analytics

# CIND 820 Learning Analytics Capstone – Milestone 2

## Project Overview

This repository contains the Milestone 2 analytical workflow for the **Learning Analytics** capstone project in **CIND 820**.

ClearStart is a proposed support tool intended to help students begin academic assignments by reducing the friction associated with task initiation. The long-term project focuses on assignment-start barriers such as confusion, overwhelm, and difficulty identifying the first step. However, because the primary TMU behavioural survey dataset is pending Research Ethics Board (REB) approval, this milestone uses the **Open University Learning Analytics Dataset (OULAD)** as a contingency dataset to develop and test the analytical pipeline.

For Milestone 2, OULAD is used to support:

- exploratory data analysis (EDA),
- data profiling and auditing,
- construction of a student-level analytical dataset,
- comparison of baseline and ensemble machine learning models, and
- development of a reproducible analytics workflow in GitHub.

---

## Project Goal

The purpose of this milestone is to build a transparent, reproducible pipeline for educational data analysis while preparing for the future ClearStart behavioural survey dataset.

Using OULAD, this project explores whether student engagement and academic performance variables can be used to identify students at greater academic risk. In the context of the broader ClearStart project, these analyses serve as a methodological and technical contingency plan while maintaining the longer-term focus on assignment initiation and student support.

---

## Repository Structure

```text
cind820-learning-analytics/
├── data/
│   ├── raw/                # Original OULAD CSV files
│   └── processed/          # Cleaned / merged student-level datasets
│
├── notebooks/
│   ├── oulad_eda.ipynb          # Data loading, profiling, merging, EDA
│   └── oulad_modeling.ipynb     # Baseline + ensemble modelling workflow
│
├── eda/
│   └── oulad_profile.html          # Optional profiling report generated from processed data
│
├── reports/
│   └── figures/                    # Figures exported for Milestone 2 report
│
├── scripts/                        # Optional helper scripts
│
├── README.md
└── requirements.txt

Dataset

Primary Planned Dataset

The long-term ClearStart project is designed around a TMU student behavioural survey focused on assignment initiation, academic overwhelm, support-seeking, and perceived barriers to starting coursework. This survey is pending REB approval and is therefore not yet available for analysis.

Contingency Dataset Used in Milestone 2

This milestone uses the Open University Learning Analytics Dataset (OULAD) as a contingency dataset to allow development of the analytical pipeline while survey data collection is pending.

OULAD paper:
Kuzilek, J., Hlosta, M., & Zdrahal, Z. (2017). Open University Learning Analytics Dataset. Scientific Data, 4, 170171. https://doi.org/10.1038/sdata.2017.171

Dataset download page:
https://analyse.kmi.open.ac.uk/open-dataset

Required OULAD Files

Download the OULAD dataset and place the following CSV files into:

```text
data/raw/

Required files:

assessments.csv
courses.csv
studentAssessment.csv
studentInfo.csv
studentRegistration.csv
studentVle.csv
vle.csv

Your folder should look like this:

```text

data/raw/
├── assessments.csv
├── courses.csv
├── studentAssessment.csv
├── studentInfo.csv
├── studentRegistration.csv
├── studentVle.csv
└── vle.csv


Analytical Workflow

This repository is organized around two notebooks.

1. oulad_eda.ipynb

This notebook performs exploratory data analysis and data preparation.

Main tasks:

load the OULAD tables,
inspect dataset structure and variable types,
merge relational tables into a student-level analytical dataset,
examine missingness and data quality,
generate univariate and bivariate visualizations,
create summary statistics for the Milestone 2 report,
optionally generate a profiling report,
save the processed dataset to data/processed/.

Outputs from this notebook may include:

data/processed/oulad_student_level.csv
figures saved in reports/figures/
optional profiling report saved in eda/

2. oulad_modeling.ipynb

This notebook performs predictive modelling using the processed student-level dataset.

Main tasks:

load the processed dataset,
define the target variable,
select and preprocess predictors,
compare baseline and ensemble models,
evaluate model performance using cross-validation.

Planned models include:

Logistic Regression (baseline)
Decision Tree (baseline)
Random Forest
XGBoost
Reproducing the Project
Option 1: Run in a local Jupyter-compatible environment

The notebooks were developed using relative paths and can be run in any Jupyter-compatible environment such as:

Jupyter Notebook
JupyterLab
VS Code notebooks

Step 1: Clone or download the repository

Clone the repo or download it as a ZIP and extract it.

Step 2: Install required packages

Install the Python dependencies listed in requirements.txt:

pip install -r requirements.txt

Step 3: Add the OULAD files

Place the required OULAD CSVs into:

data/raw/

Step 4: Run the notebooks in order

Run:

notebooks/oulad_eda.ipynb
notebooks/oulad_modeling.ipynb
Running in Google Colab

These notebooks can also be adapted for Google Colab, but a few changes are required.

Install packages in Colab

Run the following in a Colab cell:

!pip install pandas numpy matplotlib seaborn scikit-learn xgboost ydata-profiling
Update file paths

The notebooks in this repository use relative paths such as:

project_root = ".."
raw_data_path = f"{project_root}/data/raw/"

If running in Google Colab, you will likely need to:

upload the repository contents and OULAD files to Google Drive,
mount Google Drive in Colab,
change the project_root variable in the notebook to match your Drive path.

Example:

from google.colab import drive
drive.mount('/content/drive')

project_root = "/content/drive/MyDrive/cind820-learning-analytics"
raw_data_path = f"{project_root}/data/raw/"
processed_data_path = f"{project_root}/data/processed/"
fig_path = f"{project_root}/reports/figures/"
eda_path = f"{project_root}/eda/"
Outputs
Processed Data

Processed student-level datasets are saved to:

data/processed/
Figures

Charts used in the Milestone 2 report are saved to:

reports/figures/

Examples may include:

final result distribution
age band distribution
highest education distribution
click activity vs final result
assessment score vs final result
correlation heatmap
Profiling Report

If generated, the automated profiling report is saved to:

eda/oulad_profile.html
Methods Summary

This milestone uses OULAD to build and test a transparent learning analytics workflow. The modelling approach compares interpretable baseline models with more flexible ensemble methods.

Baseline models
Logistic Regression
Used as a simple, interpretable baseline for classification.
Decision Tree
Used as an explainable tree-based baseline.
Planned ensemble models
Random Forest
Used to capture non-linear relationships and interactions while reducing the instability of a single tree.
XGBoost
Used as a higher-performance gradient boosting approach for structured tabular data.
Validation strategy

Model performance is evaluated using stratified k-fold cross-validation to preserve the distribution of the outcome variable across folds.

Research Context

This repository supports the Milestone 2 requirements for:

methodological rationale and gap analysis,
data profiling and audit,
system architecture and analytical pipeline design,
reproducibility and GitHub documentation.

Although OULAD does not contain direct measures of assignment overwhelm, fear of doing tasks incorrectly, or first-step confidence, it provides a structured educational dataset that supports development of the analytical workflow while the future ClearStart behavioural survey remains pending.

Limitations of the OULAD Contingency Dataset

OULAD is useful for pipeline development, but several limitations should be noted:

it reflects data from a single institution (The Open University),
it represents an online learning context rather than a TMU context,
it does not directly measure psychological or behavioural initiation barriers,
it cannot fully answer the future ClearStart research questions related to assignment-start friction.

For these reasons, OULAD should be interpreted as a contingency dataset for methodological development rather than a substitute for the planned TMU behavioural survey.

Privacy and Ethics

OULAD is a publicly available anonymized dataset. No directly identifying personal information is included in the dataset used in this repository.

The future TMU behavioural survey component of the ClearStart project will involve human participants and will require REB approval and compliance with the Tri-Council Policy Statement: Ethical Conduct for Research Involving Humans (TCPS 2) before data collection begins.

AI Use Declaration

Generative AI tools may be used in this project for limited support purposes such as:

brainstorming repository structure,
drafting documentation,
debugging or explaining code,
suggesting analytical workflow organization.

Generative AI tools are not used to fabricate results, generate unverified findings, or replace the student’s own understanding of the analytical methods. All analysis decisions, code execution, interpretation, and written conclusions remain the responsibility of the student, who must be able to explain and justify all submitted work.

References

Arnold, K. E., & Pistilli, M. D. (2012). Course signals at Purdue: Using learning analytics to increase student success. Proceedings of the 2nd International Conference on Learning Analytics and Knowledge, 267–270. https://doi.org/10.1145/2330601.2330666

Breiman, L. (2001). Random forests. Machine Learning, 45(1), 5–32. https://doi.org/10.1023/A:1010933404324

Chen, T., & Guestrin, C. (2016). XGBoost: A scalable tree boosting system. Proceedings of the 22nd ACM SIGKDD International Conference on Knowledge Discovery and Data Mining, 785–794. https://doi.org/10.1145/2939672.2939785

James, G., Witten, D., Hastie, T., & Tibshirani, R. (2021). An introduction to statistical learning: With applications in R (2nd ed.). Springer. https://doi.org/10.1007/978-1-0716-1418-1

Kahu, E. R. (2013). Framing student engagement in higher education. Studies in Higher Education, 38(5), 758–773. https://doi.org/10.1080/03075079.2011.598505

Kotsiantis, S. B., Pierrakeas, C. J., & Pintelas, P. E. (2004). Predicting students’ performance in distance learning using machine learning techniques. Applied Artificial Intelligence, 18(5), 411–426. https://doi.org/10.1080/08839510490442058

Kuzilek, J., Hlosta, M., & Zdrahal, Z. (2017). Open University Learning Analytics Dataset. Scientific Data, 4, 170171. https://doi.org/10.1038/sdata.2017.171

Rozental, A., & Carlbring, P. (2014). Understanding and treating procrastination: A review of a common self-regulatory failure. Psychology, 5(13), 1488–1502. https://doi.org/10.4236/psych.2014.513160

Siemens, G., & Long, P. (2011). Penetrating the fog: Analytics in learning and education. EDUCAUSE Review, 46(5), 30–40.

Tinto, V. (1993). Leaving college: Rethinking the causes and cures of student attrition (2nd ed.). University of Chicago Press.
