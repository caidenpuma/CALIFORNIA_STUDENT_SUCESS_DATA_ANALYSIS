# CALIFORNIA STUDENT SUCESS METRICS DATA ANALYSIS

## Overview

This project investigates whether there is a statistically significant relationship between school transportation access—measured by the number of school buses per 1,000 students—and key educational outcomes such as graduation rates, college enrollment, and chronic absenteeism across California public school districts.

The analysis combines public datasets, applies statistical modeling, and communicates insights through both code and visualization. It was developed as a semester-long capstone project in Brown University's DATA0200 course.

---

## Research Question

> Is there a statistically significant relationship between transportation access (measured by buses per 1,000 students) and student outcomes such as graduation rates, college enrollment, or chronic absenteeism?

---

## Dataset Summary

### Data Sources

- **California Department of Education (2022)**  
  Educational outcomes including cohort sizes, graduation rates, enrollment, and absenteeism.

- **School Bus Fleet Magazine (2021–2022)**  
  Transportation data including total number of buses and bus age by school district.

### Key Variables

| Variable                      | Type        | Description                                         |
|------------------------------|-------------|-----------------------------------------------------|
| `buses_per_1000_students`    | Continuous  | Number of buses normalized by student cohort size   |
| `college_going_rate`         | Continuous  | % of cohort attending college (12-month)            |
| `chronic_absenteeism_rate`   | Continuous  | % of students missing significant instructional time|
| `grad_rate`, `dropout_rate`  | Continuous  | HS diploma and dropout metrics                      |
| `enrolled_in_state_rate`     | Continuous  | % of college-going students who stayed in-state     |

---

## Methodology

### Data Cleaning & Normalization

- Merged two datasets by district code
- Excluded districts with missing entries
- Converted all numeric data types
- Normalized outcome variables to per-cohort metrics
- Calculated `buses_per_1000_students` to standardize comparisons

### Exploratory Data Analysis (EDA)

- Histograms, boxplots, pie charts for univariate distribution
- Heatmap of Pearson correlations between all variables
- Bivariate scatterplots to assess relationships

### Statistical Modeling

- **OLS Regression** used to test significance and strength of relationships
- Independent Variable: `buses_per_1000_students`
- Dependent Variables: multiple outcome metrics (rates)
- **Assumption Tests**:
  - Shapiro-Wilk (normality)
  - Breusch-Pagan (homoscedasticity)
  - Durbin-Watson (independence)

---

## Results

### Correlation Matrix (Key Findings)

| Variable                    | Correlation | Direction        |
|----------------------------|-------------|------------------|
| College Going Rate         | -0.23       | Negative         |
| In-State Enrollment Rate   | -0.25       | Negative         |
| Chronic Absenteeism Rate   | +0.18       | Positive         |
| Not Enrolled Rate          | +0.23       | Positive         |

### OLS Regression (Significant Outcomes)

| Response Variable          | Coefficient   | p-value   | R² Adj. | Interpretation                                       |
|---------------------------|---------------|-----------|---------|------------------------------------------------------|
| College Going Rate        | -0.0441       | 0.00016   | 0.047   | More buses ⇨ lower college attendance                |
| Not Enrolled Rate         | +0.0004       | 0.00016   | 0.047   | More buses ⇨ more students not enrolled in college   |
| Chronic Absenteeism Rate  | +0.0294       | 0.00241   | 0.030   | More buses ⇨ more absenteeism                        |

### Model Assumptions

| Test                | Result                                  |
|---------------------|------------------------------------------|
| Shapiro-Wilk        | Not satisfied for all models             |
| Breusch-Pagan       | Satisfied for all but one variable       |
| Durbin-Watson       | Satisfied (all in 1.5–2.5 range)         |

> Note: Results must be interpreted cautiously due to low R² values and some assumption violations.

---

## Interpretation

Contrary to expectations, the analysis shows a **negative correlation between transportation access and positive outcomes**. This suggests that higher bus availability may be a **proxy for other challenges**—such as rurality, longer commutes, socioeconomic disadvantage, or systemic under-resourcing.

Rather than indicating a causal link, bus access likely reflects **underlying structural issues** in the district. These findings align with existing concerns about educational equity in geographically large or low-income areas.

---

## Visualizations

### Python (Seaborn & Matplotlib)
- Correlation heatmap
- Scatterplots with regression lines
- Boxplots for outcome distributions

### Tableau
Interactive Dashboard:  
📊 https://public.tableau.com/app/profile/caiden.puma/viz/ScaffoldFour/Story1?publish=yes

---
## Setup Instructions

### Prerequisits
* Google Colab programming enivornment
* Dependencies: Pandas, seaborn, matplotlib, statsmodels, scipy

### Program Run Process
* Open the main notebook directly in Google Colab:
* To run the notebook: Go to Runtime → Run all

## Limitations

- Only 2022 data used (post-COVID anomalies possible)
- District-level data limits student-level inferences
- No socioeconomic or demographic control variables included
- Bus count as a proxy variable may oversimplify true transportation access

---

## Technologies Used

- **Python**: pandas, seaborn, matplotlib, statsmodels
- **Google Colab**: main development environment
- **Tableau**: visualization and storytelling
- **LaTeX / Markdown**: reporting and formatting
