This folder is intended to store the raw Open University Learning Analytics Dataset (OULAD) CSV files used in this project.

Raw data files are not included in this repository.

To reproduce the analysis:
1. Download the OULAD dataset from the official source.
2. Place the following CSV files in this `data/raw/` folder:
   - studentInfo.csv
   - studentAssessment.csv
   - assessments.csv
   - courses.csv
   - studentRegistration.csv
   - vle.csv

Note: `studentVle.csv` is part of OULAD but was not required for the current milestone implementation because the analysis focused on demographic, course, and assessment-derived student-level features.

After placing the raw files in `data/raw/`, run:
1. `notebooks/oulad_eda.ipynb`
2. `notebooks/oulad_modelling.ipynb`
