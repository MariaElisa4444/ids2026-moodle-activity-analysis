### ids2026-moodle-activity-analysis

**Authors:** Viktorija Korjagina, Maria Elisa Vassiljeva, Kostiantyn Iliushchenko
**Course:** Introduction to Data Science (LTAT.02.002), University of Tartu, autumn 2026

**Motivation and goal.** Moodle activity of students changed a lot between 2019 and 2026 (COVID-19, different teaching formats, new tools). We use the Moodle event logs of the Theoretical Computer Science course to answer two questions:
1. How did student and teacher activity change between 2019 and 2026
2. How well can Moodle activity in the first 8 weeks predict the final numerical grade of a student, also for later cohorts.

**Data.** The data (Moodle event logs, grades and course information of 8 course years) is private and is not included in this repository. It was provided by Reimo Palm, University of Tartu.

**Files.**
- `01a_activity_analysis.ipynb`: detailed analysis of student and teacher Moodle activity from 2019 to 2026, including yearly trends, activity types and weekly patterns
- `01b_activity_deeper_analysis.ipynb`: further analysis of changes in 2023–2026, the COVID-19 transition, and activity around homework deadlines and exams
- `02_shared_dataset.ipynb`: builds the shared student-level dataset (activity features of the first 8 weeks and the final grade) and the train/test split (train: 2019 and 2021-2024, test: 2025 and 2026)
- `02_ridge_regression.ipynb`, `03_decision_tree.ipynb`, `04_random_forest.ipynb`: three prediction models, compared with a baseline that predicts the average grade
- `05_rf_experiments.ipynb`: additional experiments with other predictors, activity periods and settings
- result tables and graphs (`*_results.csv`, `*.png`)

**How to repeat the analysis.** Install Python with pandas, pyarrow, scikit-learn and matplotlib. Put `tcs_dataset/` next to the notebooks and run them in this order: `01a_activity_analysis`, `01b_activity_deeper_analysis`, `02_shared_dataset` (it creates `shared_train.csv` and `shared_test.csv`), then `02_ridge_regression`, `03_decision_tree`, `04_random_forest` and `05_rf_experiments`.

**Main results so far.** 

**Goal 1:**

Moodle activity increased significantly during the COVID-19 period (2020–2021), when teaching moved online. Activity decreased after the return to mainly in-person teaching, increased again in 2024, and then dropped sharply in 2025–2026. The unusually high activity in 2024 and the following decline were largely associated with changes in quiz-related events. However, quiz participation remained consistently high (approximately 95–97%), showing that fewer recorded events do not necessarily mean lower participation.

Student activity was consistently highest on homework deadline days, while exam-day activity was particularly high during 2020–2022. Student and teacher activity also followed different patterns, especially in grading and quiz-related activities.

**Goal 2:**

On the test years 2025 and 2026 the best model (Ridge regression) has a mean absolute error of 18.3 and 19.5 grade points, while the baseline has 20.2 and 21.0. The other models are closer to the baseline. So Moodle activity of the first 8 weeks alone predicts the final grade only weakly.
