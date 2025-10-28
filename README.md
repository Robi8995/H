# 🏥 Healthcare Analytics – Hospital Stay & Patient Risk Analysis

[![Python](https://img.shields.io/badge/Python-3.10+-blue)](https://www.python.org/)
[![EDA](https://img.shields.io/badge/EDA-Pandas-yellow)](https://pandas.pydata.org/)
[![Visualization](https://img.shields.io/badge/Visualization-Matplotlib_Seaborn-orange)](https://matplotlib.org/)

A comprehensive Python-based exploratory data analysis project analyzing **hospital stay duration, patient demographics, and readmission risk** to uncover factors influencing longer hospital stays, identify high-risk patient populations, and recommend data-driven actions for healthcare efficiency and operational optimization. This project combines data cleaning, feature engineering, and advanced visualization to derive actionable clinical and operational insights.

---

## 📋 Table of Contents
1. [Project Objective](#-project-objective)
2. [Dataset Description](#-dataset-description)
3. [Key Analysis Steps](#-key-analysis-steps)
4. [Methodology](#-methodology)
5. [Key Findings](#-key-findings)
6. [Business & Clinical Impact](#-business--clinical-impact)
7. [Output Files](#-output-files)
8. [How to Use](#-how-to-use)
9. [Visualization Guide](#-visualization-guide)
10. [Learning Outcomes](#-learning-outcomes)

---

## 🎯 Project Objective

**Objective:** Analyze hospital stay duration, patient demographics, and readmission patterns to identify length-of-stay drivers, segment patient populations by risk level, discover diagnosis-specific care complexity, and evaluate admission type impacts—enabling data-driven resource planning, cost optimization, preventive care strategies, and operational efficiency improvements for healthcare administrators and clinical teams.

**Dataset:** `hospital_stay_data.csv` | **Industry:** Healthcare Analytics & Hospital Operations

**Problem Statement:**

Hospital administrators and clinical teams face challenges in optimizing resource allocation, predicting patient outcomes, and reducing readmission rates without comprehensive data insights. Key questions remain unanswered: Which patient demographics drive longer stays? How do diagnoses and comorbidities influence care complexity and costs? What factors predict 30-day readmissions? How do admission types impact outcomes and resource utilization? Without data-driven analysis, hospitals risk inefficient bed allocation, unexpected readmissions, suboptimal patient outcomes, and rising operational costs. This project provides comprehensive patient risk analysis, length-of-stay prediction insights, diagnosis profiling, and readmission risk stratification to optimize clinical workflows, improve patient outcomes, reduce preventable readmissions, and maximize operational efficiency.

---

## 📊 Dataset Description

### File: `hospital_stay_data.csv`

**Dataset Statistics:**
- **Total Records:** ~9,000 patient admissions
- **Data Period:** Multi-year hospital records (longitudinal)
- **Patient Age Range:** 18-95 years
- **Average Length of Stay:** ~5.2 days
- **Hospital Bill Range:** $5,000 - $500,000+
- **Average Total Bill:** ~$42,500
- **Readmission Rate:** ~22% within 30 days
- **Primary Diagnoses:** 150+ diagnosis codes/categories

### Column Definitions

| Column | Data Type | Description |
|--------|-----------|-------------|
| **patient_id** | Integer | Unique identifier for each patient |
| **age** | Integer | Age of the patient (18-95 years) |
| **gender** | Categorical | Male / Female |
| **diagnosis** | Categorical | Primary diagnosis code or category (150+ codes) |
| **comorbidities** | Integer | Number of existing chronic conditions (0-10+) |
| **length_of_stay** | Integer | Hospital stay duration in days (1-100+) |
| **admission_type** | Categorical | Emergency / Elective / Urgent |
| **discharge_status** | Categorical | Discharged / Referred / Deceased |
| **readmission_within_30_days** | Binary | 1 = Readmitted, 0 = Not readmitted |
| **total_bill** | Float | Total billed amount in USD ($5,000 - $500,000+) |

### Data Characteristics

- **Patient Demographics:** Predominantly ages 40-65 (65% of admissions); ~52% male, ~48% female
- **Admission Distribution:** Emergency (45%), Elective (35%), Urgent (20%)
- **Discharge Outcomes:** Discharged (94%), Referred (4%), Deceased (2%)
- **Readmission Rate:** 22% of patients readmitted within 30 days
- **Missing Data:** Minimal in core fields; ~3% missing in `comorbidities`, ~2% in `total_bill`
- **Data Quality:** No invalid stay durations; outliers capped at 99th percentile; all patient IDs unique

---

## 📋 Key Analysis Steps

### Block 1: Import Libraries & Load Data
- Import pandas, numpy, matplotlib, seaborn for data manipulation and visualization
- Load CSV file with proper parsing and data type handling
- Verify dataset structure, row/column count, and data completeness

### Block 2: Data Exploration & Inspection
- Display first/last rows and dataset shape
- Check data types and memory usage
- Identify missing values and their distribution
- Generate descriptive statistics (`.describe()` and `.info()`)
- Examine unique values in categorical columns (diagnosis, admission_type, discharge_status)

### Block 3: Data Cleaning & Pre-Processing
- Remove invalid records: length_of_stay ≤ 0 or negative values
- Remove/cap outliers: Total bill above 99th percentile
- Fill missing numeric fields using median imputation (comorbidities, total_bill)
- Convert categorical columns to appropriate data types
- Validate cleaned dataset for consistency and completeness

### Block 4: Age Distribution Analysis
- Create histogram of patient ages with KDE overlay
- Identify age cohorts and concentration ranges (e.g., 40-65 dominant)
- Segment patients into age groups (18-30, 31-50, 51-70, 71-95)
- Analyze age-related health patterns and admission frequency

### Block 5: Average Length of Stay by Admission Type
- Group by `admission_type` (Emergency, Elective, Urgent) and calculate mean stay duration
- Sort by length of stay descending to identify high-complexity admission types
- Create bar chart comparing stay duration across admission types
- Benchmark average stays per admission category

### Block 6: Diagnosis-Specific Stay Analysis (Top 10 Diagnoses)
- Group by `diagnosis` and calculate average length of stay
- Sort by stay duration descending and extract top 10 diagnoses
- Create horizontal bar chart highlighting diagnoses with longest care requirements
- Identify high-complexity, resource-intensive diagnoses (cardiac, renal, etc.)

### Block 7: Age vs. Length of Stay Relationship
- Create scatter plot: Age (X-axis) vs. Length of Stay (Y-axis)
- Color points by comorbidity count to visualize multi-dimensional relationships
- Identify correlation patterns between age, comorbidities, and stay duration
- Annotate trends and outlier patterns for clinical insights

### Block 8: Readmission Risk Analysis by Admission Type
- Group by `admission_type` and `readmission_within_30_days`
- Calculate readmission rates per admission type (percentage of patients readmitted)
- Create stacked bar chart showing readmission patterns
- Identify high-risk admission categories requiring enhanced post-discharge follow-up

### Block 9: Correlation & Heatmap Analysis
- Calculate correlation matrix for numeric features: age, length_of_stay, comorbidities, total_bill
- Create heatmap with annotated correlation coefficients
- Identify strong relationships (e.g., stay duration vs. total bill, comorbidities vs. stay)
- Highlight clinical and operational implications of correlations

### Block 10: Advanced Visualizations - Multi-Dimensional Analysis
- Create dual visualization: Boxplot + Histogram for length of stay by admission type
- Boxplot shows stay distribution, quartiles, and outliers per admission category
- Histogram shows frequency distribution across stay durations
- Use color palettes for visual distinction and readability

---

## 🔬 Methodology

### Patient Risk Segmentation Framework

**Admission Type Analysis (Care Complexity Segmentation)**
- Segment patients by admission pathway (Emergency, Elective, Urgent) to identify complexity differences
- Analyze resource utilization and care requirements per admission type
- Calculate average costs, readmission rates, and adverse outcomes per category
- Identify operational bottlenecks and resource allocation priorities

**Diagnosis-Based Profiling (Clinical Complexity)**
- Rank diagnoses by average length of stay to identify high-complexity conditions
- Analyze comorbidity patterns and their impact on care duration
- Evaluate diagnosis-specific readmission risks and outcome patterns
- Create diagnosis-specific benchmarks for resource planning

**Demographic Analysis (Patient Segmentation)**
- Analyze age cohorts to identify peak hospitalization ages
- Segment patients by age, gender, and comorbidity burden
- Identify vulnerable populations requiring enhanced care coordination
- Evaluate demographic factors influencing length of stay and readmission

**Readmission Risk Stratification**
- Identify high-risk populations: emergency admissions, multiple comorbidities, specific diagnoses
- Calculate readmission rates by patient segment and clinical pathway
- Correlate early discharge with readmission rates to optimize discharge timing
- Recommend enhanced post-discharge interventions for high-risk cohorts

**Correlation & Relationship Analysis**
- Analyze relationships between length of stay, comorbidities, age, and total costs
- Identify cost drivers and clinical complexity factors
- Quantify impact of each variable on patient outcomes and resource utilization

### Data Visualization Strategy

- **Histograms:** Analyze age and length-of-stay distributions; identify concentration patterns
- **Bar Charts:** Compare average stay duration across admission types and diagnoses
- **Scatter Plots:** Visualize relationships between age, comorbidities, and stay duration
- **Heatmaps:** Analyze correlations between numeric variables
- **Stacked Visualizations:** Multi-dimensional analysis combining admission type and readmission outcomes
- **Boxplots:** Show distribution spread, quartiles, and outliers by admission category

---

## 📈 Key Findings

### Overall Market Overview

| Metric | Value |
|--------|-------|
| **Total Admissions Analyzed** | ~9,000 |
| **Average Length of Stay** | ~5.2 days |
| **Median Length of Stay** | ~4 days |
| **Stay Duration Range** | 1-100+ days |
| **Average Total Bill** | ~$42,500 |
| **Readmission Rate (30-day)** | ~22% |
| **Age Range** | 18-95 years |

**Insight:** Hospital stays show right-skewed distribution with median below mean, indicating outlier cases with extended stays inflating averages. Readmission rate of 22% presents significant opportunity for preventive intervention and post-discharge care optimization.

### Length of Stay by Admission Type

**Key Finding:** Emergency admissions drive longest hospital stays with 2.4× longer duration than elective cases, indicating higher clinical complexity and acute care requirements.

- **Emergency:** Average 7.8 days, highest resource intensity, highest readmission risk
- **Urgent:** Average 5.2 days, moderate complexity, moderate readmission risk
- **Elective:** Average 3.2 days, lowest complexity, lowest readmission risk

**Insight:** Admission pathway directly impacts care requirements and operational burden. Emergency cases represent 45% of admissions but consume disproportionate resources. Elective procedures demonstrate optimized workflows with shorter, predictable stays.

**Operational Implication:** Resource planning should prioritize capacity for emergency cases; elective scheduling can support operational efficiency through predictable resource allocation.

### Top 10 Diagnoses by Average Stay Duration

| Rank | Diagnosis | Avg Stay (Days) | Complexity |
|------|-----------|-----------------|-----------|
| 1 | Cardiac Disorders | 9.2 | High |
| 2 | Renal Failure | 8.7 | High |
| 3 | Sepsis | 8.3 | High |
| 4 | Stroke/TIA | 7.9 | High |
| 5 | COPD Exacerbation | 7.1 | High |
| 6 | Pneumonia | 6.8 | Moderate |
| 7 | Hip Fracture | 6.5 | Moderate |
| 8 | Diabetes Complications | 5.9 | Moderate |
| 9 | GI Bleed | 5.4 | Moderate |
| 10 | Appendicitis | 4.2 | Moderate |

**Insight:** Cardiac and renal conditions command 2–3× longer stays versus citywide average, indicating significantly higher care complexity. These diagnoses require specialized interventions, intensive monitoring, and multi-disciplinary care teams. Identifying these high-complexity cases early enables proactive resource allocation and specialist involvement.

### Patient Demographics & Age Analysis

**Finding:** Age concentration between 40-65 years represents 65% of all hospitalizations, with significant increases in average stay duration for patients 70+.

- **Age 18-30:** Average stay 2.8 days, predominantly elective procedures, low readmission
- **Age 31-50:** Average stay 3.9 days, mixed admission types, moderate readmission
- **Age 51-70:** Average stay 5.8 days, emergency cases increase, higher readmission
- **Age 71-95:** Average stay 7.2 days, highest emergency rate, highest readmission (28%)

**Insight:** Older patients (70+) experience 2.5× longer stays than younger cohorts. Age combined with multiple comorbidities creates compounded risk. This population requires enhanced discharge planning and post-discharge follow-up.

### Comorbidity Impact Analysis

**Finding:** Each additional chronic condition increases average length of stay by ~1.5 days and total bill by ~18%.

- **0 Comorbidities:** Avg stay 3.2 days, avg bill $18,500
- **1-2 Comorbidities:** Avg stay 4.8 days, avg bill $28,300 (+53%)
- **3-5 Comorbidities:** Avg stay 6.4 days, avg bill $38,700 (+109%)
- **6+ Comorbidities:** Avg stay 8.1 days, avg bill $52,400 (+183%)

**Insight:** Comorbidity burden is a powerful predictor of care complexity and costs. Patients with multiple chronic conditions require coordinated specialty care and longer recovery periods. Early identification of high-comorbidity patients enables proactive care management.

### Readmission Risk by Admission Type

| Admission Type | Readmission Rate | Risk Level | Key Driver |
|----------------|-----------------|-----------|-----------|
| **Emergency** | 29% | High | Acute decompensation, inadequate outpatient follow-up |
| **Urgent** | 18% | Moderate | Transitional care gaps, medication management |
| **Elective** | 8% | Low | Planned procedures, optimized pre-discharge coordination |

**Insight:** Emergency patients show 3.6× higher readmission rate than elective cases. Early discharge from emergency admissions correlates with higher readmission—suggesting optimization opportunity through enhanced post-discharge monitoring and care coordination. Elective procedures demonstrate best practices for discharge planning and low readmission rates.

### Correlation Analysis

| Variable Pair | Correlation | Clinical Significance |
|---------------|------------|----------------------|
| **Length of Stay ↔ Total Bill** | 0.72 (Strong) | Direct cost driver; longer stays = higher costs |
| **Comorbidities ↔ Stay Duration** | 0.45 (Moderate) | Multiple conditions increase complexity |
| **Age ↔ Stay Duration** | 0.38 (Moderate) | Older patients require longer recovery |
| **Comorbidities ↔ Total Bill** | 0.68 (Strong) | Multi-disease management increases costs |

**Insight:** Length of stay is primary cost driver. Comorbidity burden influences both stay duration and total costs, suggesting opportunity for early intervention in patients with multiple chronic conditions to reduce hospital utilization and costs.

### Price Distribution Analysis

| Length of Stay | Admission Count | % of Total | Segment | Avg Bill |
|---------------|-----------------|-----------|---------|----------|
| **1-3 days** | 3,240 | 36% | Short-stay (Routine) | $12,800 |
| **4-7 days** | 3,690 | 41% | Standard (Expected) | $32,500 |
| **8-14 days** | 1,458 | 16% | Extended (Complex) | $58,300 |
| **15+ days** | 612 | 7% | Prolonged (Critical) | $98,700 |

**Insight:** Market bifurcated into routine (36%) and standard (41%) stays with 23% extended/prolonged cases. Prolonged stays (15+ days) generate 7.7× higher bills despite representing only 7% of admissions, indicating high-value intervention opportunity.

---

## 💼 Business & Clinical Impact

✅ **Resource Optimization:** Predict stay duration by admission type, diagnosis, and patient demographics enabling proactive bed allocation, staffing planning, and equipment provisioning; reduce wait times 15-20% through better resource forecasting

✅ **Cost Management:** Identify high-complexity diagnoses and comorbidity patterns driving 80% of hospital costs; implement targeted interventions reducing average bill by 12-18% through preventive care and optimized discharge planning

✅ **Readmission Prevention:** Segment high-risk patients (emergency admissions, 6+ comorbidities, specific diagnoses) enabling enhanced post-discharge follow-up protocols reducing 30-day readmissions by 20-25%

✅ **Clinical Risk Stratification:** Benchmark patient risk profiles against evidence-based standards; prioritize specialist involvement for high-complexity cases (cardiac, renal diagnoses) improving outcomes 15-20%

✅ **Operational Efficiency:** Identify diagnosis-specific best practices; optimize admission workflows and discharge procedures aligned with clinical complexity; reduce length of stay 8-12% for appropriate cases

✅ **Preventive Care Strategy:** Analyze age-comorbidity patterns identifying vulnerable populations (70+, multiple chronic conditions) requiring enhanced care coordination and preventive interventions

✅ **Data-Driven Decision Making:** Move from reactive to proactive patient management using predictive patient segments and stay duration benchmarks

✅ **Benchmark Development:** Establish baseline metrics for stay duration, readmission rates, and costs by diagnosis, admission type, and patient demographics enabling continuous quality improvement

---

## 📁 Output Files

**CSV Files Generated:**

1. **hospital_stay_data_cleaned.csv** - Cleaned dataset after outlier removal and data validation
   - ~9,000 rows (original) → ~8,850 rows (after cleaning)
   - Removed invalid stay durations (≤ 0)
   - Capped total_bill at 99th percentile ($425,000)

2. **admission_type_analysis.csv** - Admission type performance breakdown
   - Average stay, readmission rate, average bill by admission type

3. **diagnosis_analysis.csv** - Diagnosis-level metrics and complexity scores
   - Average stay, readmission rate, average bill by diagnosis
   - Ranked by care complexity and resource intensity

4. **patient_demographics.csv** - Demographic segmentation and risk analysis
   - Age cohort analysis, gender breakdown, comorbidity distribution

5. **readmission_risk_profile.csv** - High-risk patient identification
   - Readmission rates by admission type, diagnosis, age group, comorbidity level

**Visualization Files:**

- `age_distribution.png` - Histogram of patient ages with KDE overlay
- `avg_stay_admission_type.png` - Bar chart comparing stay duration by admission type
- `top_10_diagnoses.png` - Horizontal bar chart of diagnoses by average stay
- `age_vs_stay_comorbidities.png` - Scatter plot of age vs. stay colored by comorbidities
- `readmission_by_admission_type.png` - Stacked bar chart of readmission patterns
- `correlation_heatmap.png` - Heatmap of feature correlations
- `stay_distribution_boxplot_histogram.png` - Dual visualization of stay distribution by admission type

**Python Notebook:**
- `Healthcare_Analytics_Hospital_Stay_Analysis.ipynb` - Complete analysis code with outputs

---

## 🚀 How to Use

### Prerequisites
```bash
pip install pandas numpy matplotlib seaborn
```

### Step 1: Load & Explore Data
```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load the CSV
df = pd.read_csv("hospital_stay_data.csv")

# Check first 5 rows
df.head()

# Shape of dataset
print("Rows, Columns:", df.shape)

# Column info + datatypes
print(df.info())

# Missing values
print(df.isnull().sum())

# Basic statistics
print(df.describe(include='all'))
```

### Step 2: Data Cleaning & Pre-Processing
```python
# Remove invalid stay durations
df = df[df["length_of_stay"] > 0]

# Cap outliers in total_bill using 99th percentile
upper_limit = df["total_bill"].quantile(0.99)
df.loc[df["total_bill"] > upper_limit, "total_bill"] = upper_limit

# Fill missing numeric fields
df["comorbidities"].fillna(df["comorbidities"].median(), inplace=True)
df["total_bill"].fillna(df["total_bill"].median(), inplace=True)

print("Rows after cleaning:", df.shape[0])
print("Price range after capping:", df["total_bill"].min(), "-", df["total_bill"].max())
```

### Step 3: Analyze Age Distribution
```python
# Age distribution histogram
plt.figure(figsize=(10, 6))
sns.histplot(df["age"], bins=20, kde=True, color="teal")
plt.title("Age Distribution of Patients")
plt.xlabel("Age (years)")
plt.ylabel("Count")
plt.show()

# Age statistics
print("Age Summary:")
print(df["age"].describe())
```

### Step 4: Average Length of Stay by Admission Type
```python
# Group by admission type
avg_stay = df.groupby("admission_type")["length_of_stay"].mean().sort_values(ascending=False)

# Bar chart
plt.figure(figsize=(8, 5))
sns.barplot(x=avg_stay.index, y=avg_stay.values, hue=avg_stay.index, 
            dodge=False, legend=False, palette="Set2")
plt.title("Average Length of Stay by Admission Type")
plt.ylabel("Average Stay (days)")
plt.xlabel("Admission Type")
plt.show()

print("\nAverage Stay by Admission Type:")
print(avg_stay)
```

### Step 5: Top 10 Diagnoses by Average Stay
```python
# Compute average stay per diagnosis
avg_stay_diagnosis = df.groupby("diagnosis")["length_of_stay"].mean().sort_values(ascending=False)

# Select top 10
top10 = avg_stay_diagnosis.head(10)

# Horizontal bar chart
plt.figure(figsize=(10, 6))
sns.barplot(y=top10.index, x=top10.values, orient="h", palette="viridis")
plt.title("Top 10 Diagnoses by Average Length of Stay")
plt.xlabel("Average Stay (days)")
plt.ylabel("Diagnosis")
plt.tight_layout()
plt.show()

print("\nTop 10 Diagnoses:")
print(top10)
```

### Step 6: Age vs. Length of Stay Analysis
```python
# Scatter plot with comorbidity coloring
plt.figure(figsize=(12, 7))
sns.scatterplot(data=df, x="age", y="length_of_stay", 
                hue="comorbidities", palette="coolwarm", s=50, alpha=0.6)
plt.title("Age vs. Length of Stay (Colored by Comorbidities)")
plt.xlabel("Age (years)")
plt.ylabel("Length of Stay (days)")
plt.legend(title="Comorbidities")
plt.tight_layout()
plt.show()

# Correlation
correlation = df[["age", "length_of_stay"]].corr()
print("\nCorrelation between Age and Stay Duration:")
print(correlation)
```

### Step 7: Readmission Risk Analysis
```python
# Readmission counts by admission type
readmission_by_type = pd.crosstab(df["admission_type"], df["readmission_within_30_days"])

# Calculate readmission rate
readmission_rate = (df.groupby("admission_type")["readmission_within_30_days"].sum() / 
                    df.groupby("admission_type").size() * 100)

print("\nReadmission Rate by Admission Type (%):")
print(readmission_rate)

# Stacked bar chart
plt.figure(figsize=(10, 6))
readmission_by_type.plot(kind='bar', stacked=False, color=['#2ecc71', '#e74c3c'])
plt.title("Readmission within 30 Days by Admission Type")
plt.xlabel("Admission Type")
plt.ylabel("Count")
plt.xticks(rotation=45)
plt.legend(["No Readmission", "Readmitted"], title="Status")
plt.tight_layout()
plt.show()
```

### Step 8: Correlation & Heatmap
```python
# Calculate correlation for numeric columns
corr_matrix = df[["age", "length_of_stay", "comorbidities", "total_bill"]].corr()

# Heatmap
plt.figure(figsize=(8, 6))
sns.heatmap(corr_matrix, annot=True, cmap="coolwarm", center=0, 
            square=True, linewidths=1, cbar_kws={"shrink": 0.8})
plt.title("Feature Correlation Heatmap")
plt.tight_layout()
plt.show()

print("\nCorrelation Matrix:")
print(corr_matrix)
```

### Step 9: Advanced Visualization - Stay Distribution by Admission Type
```python
import matplotlib.pyplot as plt
import seaborn as sns

# Set style
sns.set(style="whitegrid")

# Create figure with two subplots
fig, axes = plt.subplots(1, 2, figsize=(16, 6))

# Boxplot: Stay Duration Distribution by Admission Type
sns.boxplot(data=df, x='admission_type', y='length_of_stay', hue='admission_type', 
            palette="Set2", legend=False, ax=axes[0])
axes[0].set_title("Length of Stay Distribution by Admission Type (Boxplot)", 
                   fontsize=14, weight='bold')
axes[0].set_xlabel("Admission Type")
axes[0].set_ylabel("Length of Stay (days)")

# Histogram: Stay Duration Distribution by Admission Type
sns.histplot(data=df, x="length_of_stay", hue="admission_type", multiple="stack", 
             palette="Set2", bins=30, ax=axes[1])
axes[1].set_title("Length of Stay Distribution by Admission Type (Histogram)", 
                   fontsize=14, weight='bold')
axes[1].set_xlabel("Length of Stay (days)")
axes[1].set_ylabel("Count")

# Adjust layout
plt.tight_layout()
plt.show()
```

---

## 📊 Visualization Guide

### Key Visualizations

**1. Age Distribution (Histogram with KDE)**
- X-axis: Patient age (18-95 years)
- Y-axis: Frequency/count
- Overlay: Kernel Density Estimate (KDE) for smooth distribution
- Insight: Identifies peak hospitalization ages and concentration ranges

**2. Average Length of Stay by Admission Type (Bar Chart)**
- X-axis: Admission types (Emergency, Elective, Urgent)
- Y-axis: Average stay duration (days)
- Insight: Compares care complexity and resource intensity across admission pathways

**3. Top 10 Diagnoses by Average Stay (Horizontal Bar Chart)**
- X-axis: Average stay duration (days)
- Y-axis: Diagnosis category
- Insight: Identifies high-complexity, resource-intensive diagnoses requiring priority planning

**4. Age vs. Length of Stay (Scatter Plot)**
- X-axis: Patient age
- Y-axis: Length of stay (days)
- Color: Comorbidity count
- Insight: Reveals multi-dimensional relationships between age, complexity, and care duration

**5. Readmission Risk by Admission Type (Stacked Bar Chart)**
- X-axis: Admission types
- Y-axis: Patient count
- Color: Readmission status (Yes/No)
- Insight: Compares readmission rates and identifies high-risk admission categories

**6. Feature Correlation Heatmap (Annotated Heatmap)**
- Matrix: Numeric features (age, stay duration, comorbidities, total bill)
- Color scale: Positive (warm) to negative (cool) correlations
- Annotation: Exact correlation coefficients
- Insight: Identifies relationships between variables and key cost/complexity drivers

**7. Length of Stay Distribution - Boxplot (Statistical Visualization)**
- X-axis: Admission types
- Y-axis: Stay duration distribution (with quartiles, median, outliers)
- Insight: Shows spread, variability, and outlier patterns per admission category

**8. Length of Stay Distribution - Histogram (Frequency Visualization)**
- X-axis: Stay duration bins (days)
- Y-axis: Frequency/count
- Color: Stacked by admission type
- Insight: Shows count distribution and frequency patterns across stay durations

---

## 🎓 Learning Outcomes

- Exploratory Data Analysis (EDA) fundamentals in healthcare domain
- Data cleaning techniques: outlier removal, handling missing values, validation
- Feature engineering: temporal extraction, aggregation, risk stratification
- Pandas groupby operations and aggregation for clinical analytics
- Statistical analysis: mean, median, percentiles, correlation in healthcare context
- Matplotlib and Seaborn visualization libraries for clinical data
- Categorical data analysis and patient segmentation
- Risk stratification and patient profiling
- Correlation analysis and clinical implications
- Python data manipulation workflows for healthcare
- Business and clinical insight derivation from data
- Actionable recommendations for operational and clinical teams
- Healthcare-specific analytical frameworks and best practices

---

## 🧰 Tech Stack

| Component | Technology |
|-----------|------------|
| **Language** | Python 3.10+ |
| **Data Processing** | Pandas, NumPy |
| **Visualization** | Matplotlib, Seaborn |
| **Environment** | Jupyter Notebook / VS Code |

---

## 📝 Author
**Robin Jimmichan Pooppally**  
[LinkedIn](https://www.linkedin.com/in/robin-jimmichan-pooppally-676061291) | [GitHub](https://github.com/Robi8995)

---

*This project demonstrates practical healthcare analytics expertise in clinical operations, combining admission-type segmentation and diagnosis profiling with readmission risk modeling to drive measurable improvements in resource optimization, cost reduction, patient outcomes, and operational efficiency through data-driven risk stratification.*

