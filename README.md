# BigBite HR Analytics Dashboard

An interactive Power BI dashboard that turns 161 employee records into a clear picture of workforce makeup, pay, age structure, and unused leave.

![BigBite HR Analytics Dashboard](images/overview-dashboard.png)

## TABLE OF CONTENTS

- [Overview](#overview)
- [Data Source](#data-source)
- [Tools](#tools)
- [Data Processing](#data-processing)
- [Skills Demonstrated](#skills-demonstrated)
- [Objectives / Problem Statement](#objectivesproblem-statement)
- [Data Analysis and Visualization](#data-analysis-and-visualization)
- [Insights](#insights)
- [Recommendations](#recommendations)

## Overview

BigBite employs 161 people across ten roles, from packaging and production to research, sales, and marketing. HR needs a fast read on who the workforce is, how it is paid, and where risk is building. This dashboard gives that read on a single page.

It covers four areas. Workforce makeup by role, gender, and education. Age structure and distance from retirement. Pay across qualification levels. Unused leave.

### At a glance

| Metric | Value |
|---|---|
| Headcount | 161 |
| Average salary | 54.23K |
| Average leave balance | 16.42 days |
| Staff with more than 20 leave days | 29 |

### What is in this repository

```
bigbite-hr-analytics/
  README.md
  data/
    hr-data.xlsx
  powerbi/
    BigBite_HR_Analytics.pbix
  images/
    overview-dashboard.png
```

## Data Source

The data is a public sample HR dataset for BigBite. 

The workbook `hr-data.xlsx` holds one sheet with 161 rows and 9 columns. Join dates run from April 2017 to June 2023. All employee names are fictional.

| Column | Description | Type |
|---|---|---|
| Name | Employee name (fictional) | Text |
| Emp ID | Unique employee identifier | Text |
| Gender | Female or Male | Text |
| Education Qualification | High School Diploma, Diploma, Bachelor's Degree, or Master's Degree | Text |
| Date of Join | Date the employee joined | Date |
| Job Title | One of ten roles | Text |
| Salary | Annual salary | Whole number |
| Age | Age in years | Decimal |
| Leave Balance | Unused leave days | Whole number |

The file is a single snapshot. It has no exit dates and no performance scores. The analysis describes the current workforce and cannot measure turnover or performance.

## Tools

| Tool | Use |
|---|---|
| Microsoft Excel | Source data file |
| Power BI Desktop | Data model, visuals, and layout |
| DAX | KPI measures |

## Data Processing

The file needed no cleaning. It has no missing values, no duplicate rows, and 161 unique Emp IDs.

The dashboard loads the workbook into Power BI and builds four KPI measures on top of the table.

```
HeadCount = COUNTROWS('data')

Avg Salary = AVERAGE('data'[Salary])

Avg Leave Balance = AVERAGE('data'[Leave Balance])

LBL Over 20 Days = CALCULATE(COUNTROWS('data'), 'data'[Leave Balance] > 20)
```

`CALCULATE` narrows the table to employees with more than 20 leave days first. `COUNTROWS` then counts what is left. The other three measures aggregate the full table.

Ages of 60 and above are read against Ghana's statutory retirement age of 60, set under the National Pensions Act 2008 (Act 766).

## Skills Demonstrated

- Power BI dashboard design and layout
- DAX measures, including filtered counts with `CALCULATE`
- KPI selection for an HR audience
- Data profiling and quality checks
- HR analytics, including workforce composition, retirement exposure, and leave liability
- Applying local regulatory context (Ghana's retirement age) to a workforce question
- Turning charts into written insights and actions

## Objectives/Problem Statement

HR leadership at BigBite needs one view of the workforce. The dashboard was built to answer five questions.

1. Who works at BigBite, and how is the workforce split by role, gender, and education?
2. How old is the workforce, and how many people are at or past retirement age?
3. How is pay spread, and does qualification explain it?
4. How much unused leave is the company carrying?
5. Which of these findings call for action?

## Data Analysis and Visualization

The page reads left to right. KPI cards sit in a rail on the left. Composition visuals run across the top. Pay and age detail sit below.

| Visual | What it shows | Why it was chosen |
|---|---|---|
| KPI cards | Headcount, average salary, average leave balance, staff over 20 leave days | Gives the four headline numbers before any detail |
| Employee Role bar chart | Headcount for each of the ten roles | Bars rank roles from largest to smallest at a glance |
| Gender pie chart | 88 female (55%) and 73 male (45%) | Two categories only, so a pie stays readable |
| Age Distribution histogram | Count of staff by age band | Shows the shape of the age structure, including the older tail |
| Qualification vs Salary scatter | Each employee as a dot, colored by education level | Shows the full spread of pay and how much levels overlap |
| Age Distribution by Gender | The same histogram split by female and male | Checks whether the age pattern differs between genders |

## Insights

1. **The workforce is front-line heavy.** Packaging Associate (22) and Production Operator (20) are the two largest roles. Together they are 42 of 161 staff, or 26%. Marketing Manager and Marketing Specialist are the smallest at 10 each.

2. **Women are a slim majority.** There are 88 women (55%) and 73 men (45%). Both genders peak in the same age band, with 44 women and 41 men in the tallest bar.

3. **The age structure is narrow.** About 71% of staff (115 of 161) are in the 31 to 40 band. Only 5 people are aged 41 to 50 and only 5 are aged 51 to 60. Few mid-career staff sit between the large group in their 30s and the oldest group.

4. **Nine employees are at or past retirement age.** That is 5.6% of staff aged 60 or above, spread across several roles. They are still on payroll today, so this is a current succession question and not a future projection.

5. **Education levels are spread evenly.** Bachelor's Degree holders number 49 (30%), High School Diploma 42 (26%), Diploma 41 (25%), and Master's Degree 29 (18%). No single level dominates.

6. **Qualification does not set pay on its own.** Master's holders earn the most on average at about 67.0K, against 53.9K for Bachelor's, 51.0K for Diploma, and 48.9K for High School Diploma. The ranges overlap heavily though. Salaries run from 28.9K to 85K, and High School Diploma holders reach 79.3K while some Master's holders start at 35.5K.

7. **Unused leave is a company-wide pattern.** Average leave balance is 16.42 days. Twenty-nine staff (18%) hold more than 20 days. They appear in all ten roles, with the most in Packaging Associate (6), Chocolatier (5), and Research Scientist (4).

## Recommendations

1. **Start succession planning now.** Name successors and document the knowledge held by the nine employees at or past 60, beginning with senior roles.

2. **Set a leave policy.** Use a carry-over cap, scheduled leave windows, or a payout rule for balances above 20 days. Unused leave builds a financial liability and can signal overwork.

3. **Build a mid-career hiring pipeline.** With only 10 staff aged 41 to 60, experienced hires would balance an age structure that leans heavily on one band.

4. **Publish the pay structure.** Qualification overlaps widely across pay levels, so link pay to role grade in writing and review cases where the structure is unclear.

5. **Collect exit dates and performance ratings.** Today's file cannot show turnover or performance. Adding both fields would allow attrition and performance analysis in a later version.

---

Built by Abdul-Mu'min Salley Adagang, Data Analyst, Kumasi, Ghana.
