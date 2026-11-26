### ids2026-moodle-activity-analysis

**Authors:** Viktorija Korjagina, Maria Elisa Vassiljeva, Kostiantyn Iliushchenko
**Course:** Introduction to Data Science (LTAT.02.002), University of Tartu, autumn 2026

**Motivation and goal.** Moodle activity of students changed a lot between 2019 and 2026 (COVID-19, different teaching formats, new tools). We use the Moodle event logs of the Theoretical Computer Science course to answer two questions:
1. How did student and teacher activity change between 2019 and 2026
2. How well can Moodle activity in the first 8 weeks predict the final numerical grade of a student, also for later cohorts.

**Data.** The data (Moodle event logs, grades and course information of 8 course years) is private and is not included in this repository. It was provided by Reimo Palm, University of Tartu.

**Files.**
- `01_data_preparation.ipynb`: combines the event logs of all years and counts events and students per year
- `week1_activity_analysis.ipynb`: analysis of activity changes over the years (activity types, weekly patterns, graphs)
- `02_shared_dataset.ipynb`: builds the shared student-level dataset (activity features of the first 8 weeks and the final grade) and the train/test split (train: 2019 and 2021-2024, test: 2025 and 2026)
- `02_ridge_regression.ipynb`, `03_decision_tree.ipynb`, `04_random_forest.ipynb`: three prediction models, compared with a baseline that predicts the average grade
- `05_rf_experiments.ipynb`: additional experiments with other predictors, activity periods and settings
- result tables and graphs (`*_results.csv`, `*.png`)

**How to repeat the analysis.** Install Python with pandas, pyarrow, scikit-learn and matplotlib. Put `tcs_dataset/` next to the notebooks and run them in this order: `01_data_preparation`, `week1_activity_analysis`, `02_shared_dataset` (it creates `shared_train.csv` and `shared_test.csv`), then `02_ridge_regression`, `03_decision_tree`, `04_random_forest` and `05_rf_experiments`.

**Main results so far.** On the test years 2025 and 2026 the best model (Ridge regression) has a mean absolute error of 18.3 and 19.5 grade points, while the baseline has 20.2 and 21.0. The other models are closer to the baseline. So Moodle activity of the first 8 weeks alone predicts the final grade only weakly. Student activity was clearly lower in 2025 and 2026 than in earlier years.
