#  Diabetes Medication Clinical Trial — Exploratory Data Analysis & Statistical Testing

An end-to-end data analysis project investigating the efficacy, demographic variations, and safety profile of a novel diabetes medication vs. placebo over a 24-week clinical trial.

##  Executive Summary

This study analyzes longitudinal clinical trial data ($N = 1,400$ total observations) to evaluate whether a new diabetes medication outperforms a placebo in lowering HbA1c levels (glycated hemoglobin).

## Key Clinical Takeaways

- Primary Efficacy: The treatment group achieved a statistically significant reduction in HbA1c compared to placebo ($p < 0.001$).
- Time to Effect: The steepest decrease in HbA1c occurred within the first 4 weeks of treatment, indicating rapid onset.
- Demographics: Medication efficacy remained consistent across age groups (Middle-aged vs. Older adults), with no notable interaction between diabetes duration and HbA1c reduction.
- Safety & Tolerability: Reported adverse events (Fatigue, Nausea, Headache, Dizziness) were evenly distributed between treatment and placebo arms ($p = 0.327$), indicating a strong safety profile not driven by medication toxicity.

##  Data Stack & Libraries

- Language: Python 3.xData Processing: pandas, numpy
- Data Visualization: matplotlib, seabornStatistical 
- Inference & Modeling: scipy.stats (T-test, Chi-Square), statsmodels (Two-Way OLS / ANOVA)

##  Analysis Pipeline & Methodology

1. Data Cleaning & Feature Engineering
- Missing Value Handling: Profiling non-null entries and removing incomplete adverse event tracking entries.
- Variable Transformation: One-hot encoding categorical treatments (group_treatment), casting numerical columns (time, hba1c), and binning continuous age into Young (<30), Middle-aged (30-60), and Old (>60).
- Within-Subject Metrics: Engineered hba1c_change by calculating difference from baseline HbA1c for every individual subject.

2. Primary Statistical Hypotheses & Results

A. Two-Sample Independent T-Test (Final HbA1c Comparison)
- Objective: Test if mean HbA1c differs between Treatment (7.36%) and Placebo (8.14%).
- Result: t = -6.200, p = 2.055 × 10⁻⁹
- Conclusion: Reject $H_0$. The treatment group experienced a statistically significant lower HbA1c level compared to placebo.

B. OLS Two-Way ANOVA Model (hba1c ~ time + group_treatment)
- Objective: Assess the main effects of time and treatment assignment on HbA1c levels.
- Conclusions: Both treatment type and time on trial independently drive significant reductions in HbA1c (p<0.001).

C. Chi-Square Test of Independence (Adverse Event Profiling)
- Objective: Test if adverse event frequencies depend on treatment vs placebo allocation.
- Result: $\chi^2 = 3.453$, $\text{dof} = 3$, $p = 0.3269$

D. Correlation Analysis (Disease Duration vs. Response)Pearson Correlation ($r$): $-0.0109$
- Conclusion: Zero linear relationship between years living with diabetes and degree of HbA1c reduction.

##  Key Visualizations

1. Longitudinal Trajectory Plot (lineplot): Illustrates the trajectory of HbA1c over 24 weeks, highlighting rapid early reduction in the treatment group.
2. Distribution Boxplots (boxplot): Compares final HbA1c levels and evaluates age-group variance.
3. Adverse Event Breakdown (barplot): Identifies top side effects across trial participants.
4. Scatterplot (scatterplot): Maps baseline HbA1c against overall $\Delta \text{HbA1c}$.

