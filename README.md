# Bellabeat Case Study: Analyzing Fitbit Data with Python

An exploratory analysis of Fitbit recording patterns, feature coverage, and daily activity to develop ideas for Bellabeat to test.

**Author:** Fitri Apriyani  
**Tools:** Python, pandas, Matplotlib, seaborn, and Jupyter notebooks in VS Code

## Project Overview

Bellabeat develops health-focused products for women. In this case study, I take on the role of a junior data analyst and use publicly available Fitbit data to explore wellness-tracking habits and propose marketing and engagement ideas for Bellabeat.

The business task is to identify smart-device usage patterns that could inform a marketing strategy for a Bellabeat product. The findings are exploratory and require validation with Bellabeat's own customers.

## Business Questions

1. How consistently do Fitbit participants record their activity?
2. How does recording frequency relate to their steps and active minutes?
3. How could Bellabeat use these findings to develop and test a marketing idea?

The analysis presented here focuses on recorded days, average daily steps, feature coverage, weight records, and sleep-record availability.

## Dataset & Tools

**Source:** [Fitbit Fitness Tracker Data by Mobius on Kaggle](https://www.kaggle.com/datasets/arashnic/fitbit)

The files analyzed contain records from **35 participants** across **33 calendar days**, from **March 11 to April 12, 2016**. Participant coverage varies by date and file.

The 11 CSV files cover daily activity, hourly and minute-level calories, intensities and steps, minute-level METs, sleep, heart rate, and weight.

| Tool | Purpose |
| --- | --- |
| Python and pandas | Data cleaning, aggregation, merging, and analysis |
| Matplotlib and seaborn | Charts and visual communication |
| Jupyter notebooks in VS Code | Exploratory analysis and documentation |

## Data Preparation & Analysis

- Converted date and time columns to datetime and standardized column names to snake_case.
- Removed duplicate records, including **525 duplicate rows** from the minute-level sleep file.
- Normalized timestamps to calendar dates and counted distinct user–date pairs across all 11 files to calculate recorded days per participant.
- Classified participants as low usage (below the first quartile), moderate usage (from the first through the third quartile), or high usage (above the third quartile).
- Counted unique participants in each file to compare feature coverage.
- Compared recorded days with **average steps per recorded activity day**, reducing the accumulation bias that would arise from using total steps.
- Examined weight-entry methods and categorized participants using their average BMI.
- Compared dates with more than zero steps against dates with sleep records to identify activity days without corresponding sleep data.

Here, “usage” means the presence of records in the dataset; it does not directly measure app engagement or continuous device wear.

## Key Findings

### 1. Moderate-usage participants formed the largest group

**54.3%** of participants fell into the moderate-usage category. High-usage participants formed the smallest group. These categories describe relative recording frequency within this sample, based on quartile thresholds.

### 2. Activity files had broader coverage than sleep, heart rate, and weight

| Feature or file group | Unique participants |
| --- | ---: |
| Daily activity | 35 |
| Each hourly or minute-level activity file: calories, intensities, steps, and METs | 34 |
| Sleep | 23 |
| Heart rate | 14 |
| Weight | 11 |

Weight had the lowest participant coverage. Heart rate was not explored further because its second-level records were outside the scope of this analysis.

### 3. Recorded days were positively associated with average daily steps

There was a **moderate positive correlation (r = 0.41)** between recorded days and average daily steps. Participants with more recorded days tended to record higher average step counts.

This association does not establish whether consistent tracking encouraged activity or whether more active participants were more likely to record data regularly.

### 4. Most weight-tracking participants used manual entry

Of the **11 participants** with weight records, **9 used manual entry** and **2 used a non-manual method**. Each participant had only one recorded input method in this file.

Also, **63.6%** had an average BMI in the overweight or obesity range. Since BMI was unavailable for participants without weight records, this does not show that people in these categories were more likely to use weight tracking.

Manual-entry effort is a possible barrier to investigate; the dataset cannot confirm why weight coverage was low.

### 5. Sleep records were missing on some activity days

Sleep-record availability varied between participants. The following examples are from the 10 users with the highest total activity days:

- Participant `2347167796` had sleep records on all **14 activity days**.
- Participant `4020332650` had sleep records on **15 of 32 activity days**.
- Several participants had activity days without any corresponding sleep records.

A missing sleep record does not mean a participant did not sleep. Device wear, charging, syncing, or dataset availability could affect these records, but the data do not establish the cause.

## Recommendations

These are ideas for Bellabeat to test, rather than proven solutions.

1. **Help users build regular tracking habits.** Test gentle reminders or weekly progress summaries and measure whether users return more often.
2. **Investigate barriers to sleep tracking.** Ask users about comfort, battery life, and syncing before deciding which improvements to prioritize.
3. **Reduce the effort of recording weight.** Test simpler manual entry and investigate whether effort, interest, or other factors affect participation.
4. **Test a campaign about healthier daily habits.** Present Bellabeat as a guide to movement, rest, and self-care, supported by short educational content and daily app reminders. Measure whether the campaign encourages app trials and continued use.

## Limitations

- The sample is small: **35 participants over 33 calendar days**.
- The records are from **2016** and may not reflect current wearable-device habits.
- Demographic information, including age and gender, is unavailable.
- The data come from Fitbit participants, not Bellabeat customers.
- Coverage varies across files, and missing records do not establish non-use of a feature.
- Usage groups are relative to this sample and are not universal engagement benchmarks.
- Correlation does not establish causation, and the dataset does not explain participants' motivations or barriers.

The findings should guide further research and testing rather than be generalized to all Fitbit or Bellabeat users.


## Project Files

| File | Description |
| --- | --- |
| `Analysis_2_Fitbit_Usage.ipynb` | Analysis of recorded days and classification of participants into low-, moderate-, and high-usage groups |
| `Analysis_1_numbers_of_users_by_feature.ipynb` | Comparison of participant coverage across Fitbit data files |
| `Analysis_3_Relationship_Steps_and_Recorded_Days.ipynb` | Relationship between recorded days and average daily steps |
| `Analysis_4_Manual_and_Non_Entries.ipynb` | Analysis of manual and non-manual weight entries |
| `Analysis_5_Classifying_Users_by_BMI.ipynb` | BMI classification among participants with weight records |
| `Analysis_6_Total_Usage_Days_vs_Sleep Usage.ipynb` | Comparison of activity days and sleep-record availability |

## Visualizations

The following visualizations highlight key patterns identified throughout the analysis.

### 1. Fitbit User Usage Level Distribution

Shows the distribution of participants across low, moderate, and high usage categories.
![Fitbit User Usage Distribution](Bellabeat%20Visualization/distribution-of-users-chart.png)

### 2. Participant Coverage Across Fitbit Features

Compares the number of unique participants recorded in each Fitbit data file.
![Number of Users by Features](Bellabeat%20Visualization/number-of-users-by-features.png)

### 3. Recorded Days vs. Average Daily Steps

Illustrates the relationship between tracking frequency and average daily steps, showing a moderate positive correlation (r = 0.41).
![Correlation Chart](Bellabeat%20Visualization/correlation-chart.png)

### 4. Weight-Logging Method Among Users

Compares manual and non-manual weight entries among the 11 participants with weight records.
![Weight Logging Method](Bellabeat%20Visualization/weight-logging-method-chart.png)

### 5. BMI Distribution Among Weight-Logging Users

Shows the BMI categories among participants who recorded their weight.
![BMI Distribution](Bellabeat%20Visualization/bmi-distribution-chart.png)

### 6. Activity Days vs. Sleep-Record Availability

Compares activity days with and without matching sleep records among the 10 participants with the highest number of activity days. This focused visualization highlights differences in sleep-tracking consistency and does not represent all participants.
![Sleep Records Availability](Bellabeat%20Visualization/sleep-records-are-missing.png)

## Full Article

Read the full analysis, including code and visualizations, on Medium:

[Bellabeat Case Study: Analyzing Fitbit Data with Python](https://medium.com/@fiapriyani77/bellabeat-case-study-analyzing-fitbit-data-with-python-e94c47bed778)

## References

- [Fitbit Fitness Tracker Data — Mobius, Kaggle](https://www.kaggle.com/datasets/arashnic/fitbit)
- [Fitabase Fitbit Data Dictionary](https://www.fitabase.com/media/2101/fitabase-fitbit-data-dictionary-as-of-11325.pdf) — Used to interpret the `IsManualReport` field in the weight log dataset.
- [BMI cutoffs according to WHO standards](https://gateway.euro.who.int/en/indicators/mn_survey_19-cut-off-for-bmi-according-to-who-standards/)

