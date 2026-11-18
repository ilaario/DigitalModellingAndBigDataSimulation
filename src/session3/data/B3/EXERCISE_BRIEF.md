# Group exercise: from raw data to a trustworthy model

Your group has received **its own dataset** from the energy, sustainability or mobility domain. It contains **one
target** (see the table below) that you will predict in Part 2. Like real-world data, your file is **not clean**.
Finding and fixing its problems is a central part of the work. Every group's data has different problems, so you'll
need to find your own solutions. There is no description of the columns: work out what they mean from their names
(units are in the names) and from what you know about the topic.

| Topic | Target column | Task | Note |
|---|---|---|---|
| A Air quality, Beijing | `high_pm25` | classification | 1 if the daily mean PM2.5 concentration is above 75 µg/m³ |
| B CO₂ of new cars | `co2_wltp_g_km` | regression | pure battery-electric and fuel-cell cars are not included |
| C Bike-sharing trips, New York | `is_member` | classification | 1 if the rider has a membership |
| D Electricity load | `load_mw` | regression | national load of one country |

Every file has a column **`split`** (`train` / `test`). It defines your train/test split for Part 2.
Every file also has a column **`timestamp`**. Time features such as hour, weekday or month are not included: derive
them from `timestamp` yourself.

## Part 1 — Exploratory Data Analysis (due Session 7, Mon 14.12.2026)

Hand in one Jupyter notebook (run top to bottom without errors) plus your cleaned dataset.

1. **Data understanding:** a data dictionary (column, type, unit, what you think it means, plausible range, share of
   missing values). Which columns don't look the way you'd expect?
2. **Data quality & cleaning:** find the problems in your data and fix them. Keep a **cleaning log** (table: problem ·
   how you found it · how many rows · what you did · why).
3. **Visual exploration:** at least
   - the distribution of the target and of the most important features,
   - the relationship of at least three features with the target,
   - **one plot over time** (e.g. the average target per hour or month, derived from `timestamp`),
   - **one plot over location** *if your data has a location column* (a map or a comparison between stations).
4. **Findings:** 3–5 short findings in plain language, and a list of features you expect to be useful for predicting
   the target (with a reason).
5. Save your cleaned data as `cleaned.csv`. You'll use it in Part 2.

## Part 2 — Machine learning (due Session 10, Tue 26.01.2027)

1. **Set-up:** state the target and the task type; split your data using the `split` column.
2. **Baseline:** a very simple reference (regression: always predict the training mean; classification: always
   predict the most frequent class). Report its metrics.
3. **Models:** train **at least two** different models (e.g. linear/logistic regression and a random forest). Use only
   the training data for any choices you make.
4. **Evaluation:** report the right metrics on the test set (regression: MAE, RMSE, R²; classification: confusion
   matrix, precision, recall, F1). Compare them with the baseline.
5. **Suspiciously good features:** is any feature *too* good? For each strong feature, answer: *would I actually know
   this value at the moment I want to make the prediction?* Train your model with and without it and explain your
   decision.
6. **Split experiment:** train your best model a second time with a plain random `train_test_split`, ignoring the
   `split` column. Compare the scores and explain *why* they differ. Which number should you report?
7. **Error analysis:** where is your best model wrong? Break the errors down by at least one category (e.g. hour,
   month, station, fuel type).
8. **Conclusion:** would you trust this model? For what would you use it, and for what not?

**Final report:** one notebook (or notebook + short PDF) covering Parts 1 and 2, including what you changed in your
cleaning after Part 1 and why.

**Grading:** Part 1 is graded from your submission. In Session 10 you'll have a **personal interview** with the
instructor: you present your findings (no slides required; your notebook is enough) and answer questions about both
parts. Parts 1 and 2 are graded together in the interview. Every group member should be able to explain **what you
intended to do, why, and what your results mean**.

**AI assistants** are allowed and encouraged, including for writing code. You don't need to explain every line of
code, but you must understand what each step does and be able to judge whether the result makes sense. Never paste
anything other than your course data into external tools.
