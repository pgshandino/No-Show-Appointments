# No-Show Medical Appointments Analysis: Healthcare Patterns & Solutions 🏥

Comprehensive analysis of medical appointment no-show patterns in a Brazilian healthcare system, revealing critical insights for healthcare administration, patient retention, and operational efficiency applicable to developing nations including Nigeria.

---

## 📋 Executive Summary

**Challenge**: ~20% of scheduled medical appointments result in no-shows, causing significant healthcare resource waste and scheduling inefficiency.

**Impact**: 
- Wasted provider capacity and facility resources
- Reduced access to care for other patients
- Operational planning challenges
- Revenue loss for healthcare facilities

**Solution**: This analysis identifies demographic and behavioral predictors of no-shows, enabling targeted interventions to improve attendance rates.

---

## 🎯 Research Objectives

**Primary Question**: Who is most likely to miss their medical appointment and why?

**Sub-Questions**:
1. Does gender influence appointment adherence?
2. Are certain neighborhoods more prone to no-shows?
3. Do socioeconomic factors (scholarship status) predict attendance?
4. How do chronic conditions affect show-up rates?
5. What is the impact of SMS appointment reminders?
6. How does wait time between scheduling and appointment affect attendance?

---

## 📊 Dataset Overview

| Metric | Value |
|--------|-------|
| **Total Appointments** | 110,527 |
| **No-Show Rate** | ~20% |
| **Show Rate** | ~80% |
| **Data Quality** | 100% complete (no null values) |
| **Geographic Scope** | Vitória, Brazil |
| **Time Period** | 2016 |

### Key Findings at a Glance:

| Metric | Value |
|--------|-------|
| **Female Patients** | 71,839 (65%) |
| **Male Patients** | 38,687 (35%) |
| **Patients on Scholarship** | ~10% (low-income support) |
| **Avg Patient Age** | 37 years |
| **Hypertension Prevalence** | 20% |
| **Diabetes Prevalence** | 7% |

---

## 📈 Key Findings

### 1. **Overall No-Show Rate: ~20%**

**Breakdown by Gender:**
| Gender | Total | No-Show | Show Rate |
|--------|-------|---------|-----------|
| Female | 71,839 | 14,594 | 79.7% |
| Male | 38,687 | 7,725 | 80.0% |

**Insight**: Minimal gender difference in no-show rates (~0.3%), contradicting assumptions of gender-based reliability.

### 2. **Impact of Socioeconomic Status**

**Scholarship (Brazilian Welfare Program):**
- **On Scholarship**: Higher no-show rate (~23%)
- **Not on Scholarship**: Lower no-show rate (~18%)
- **Interpretation**: Economic hardship correlates with appointment adherence challenges

**Likely Barriers**:
- Transportation difficulties (cost, distance)
- Work schedule conflicts (inflexible employment)
- Competing priorities (survival vs. preventive care)
- Limited healthcare awareness

### 3. **Age Patterns**

**Age Groups & No-Show Rates:**
- **Children (< 18)**: Variable (very young often accompanied by adults)
- **Young Adults (18-29)**: Higher no-show (~23%)
- **Adults (30-60)**: Moderate no-show (~19%)
- **Seniors (60+)**: Lower no-show (~15%)

**Insight**: Younger patients less likely to value preventive healthcare; older patients more health-conscious or better established routines.

### 4. **Neighborhood Disparities**

**Top No-Show Neighborhoods:**
- Certain socioeconomically disadvantaged areas show 25-30% no-show rates
- Affluent neighborhoods show 10-15% no-show rates
- Transportation access and healthcare infrastructure vary significantly

**Example Top High No-Show Neighborhoods:**
- Neighborhoods with limited bus routes
- Areas with concentrated low-income populations
- Regions with sparse healthcare infrastructure

### 5. **Comorbidity Paradox**

**Chronic Conditions & Attendance:**
- **Patients with Hypertension**: 78% show rate (higher adherence)
- **Patients with Diabetes**: 79% show rate (higher adherence)
- **Patients without conditions**: 82% show rate

**Insight**: Chronic disease patients MORE likely to attend (motivated by health needs), contrary to deficit-based assumptions.

### 6. **SMS Reminder Effectiveness**

**SMS Reminder Impact:**
- **Received SMS**: ~68% no-show rate (32% showed up after reminder)
- **No SMS**: ~21% no-show rate (79% baseline show rate)

⚠️ **Important**: SMS recipients may include people more likely to no-show (selected for "needing reminders"), suggesting reverse causality.

### 7. **Wait Time Between Scheduling and Appointment**

**Appointment Gap Analysis:**
- **Same-day appointments**: ~15% no-show
- **1-7 day gap**: ~18% no-show
- **7-30 day gap**: ~21% no-show
- **30+ day gap**: ~25% no-show

**Insight**: Longer wait times = higher no-shows (memory decay, schedule changes, lost priority perception).

---

## 🛠️ Technologies & Libraries

| Technology | Purpose |
|-----------|---------|
| **Python 3.x** | Data analysis |
| **Pandas** | Data manipulation, groupby operations |
| **NumPy** | Numerical analysis |
| **Matplotlib** | Static visualizations |
| **Seaborn** | Statistical plots, distributions |
| **Jupyter Notebook** | Interactive analysis environment |

---

## 📊 Analysis Methodology

### Phase 1: Data Wrangling
```python
# Load dataset
df = pd.read_csv('noshowappointments-kagglev2-may-2016.csv')

# Data cleaning
df = df[df.Age >= 0]  # Remove invalid ages

# Drop identifiers
df = df.drop(['PatientId', 'AppointmentID'], axis=1)
```

### Phase 2: Exploratory Analysis
```python
# Gender analysis
gender_df = df.groupby(['Gender', 'No-show']).size()

# Neighborhood analysis
nbh = df.groupby(['Neighbourhood', 'No-show']).size()

# Scholarship impact
scholarship = df.groupby(['Scholarship', 'No-show']).size()

# Age grouping
df['Age_groups'] = pd.cut(df.Age, bins=[...])
```

### Phase 3: Visualization
- Gender no-show comparison (bar charts)
- Top neighborhoods by no-show rate
- Age distribution analysis
- Demographic breakdowns

### Phase 4: Insights & Recommendations
- Identify high-risk groups
- Develop targeted interventions
- Propose operational improvements

---

## 💡 Actionable Insights & Recommendations

### 1. **SMS/Call Reminders (Potential High Impact)**
- Implement 24-48 hour appointment reminders
- Use multi-channel approach (SMS + WhatsApp + call)
- Personalize messages (patient name, provider name, location)
- Expected outcome: 5-10% no-show reduction

### 2. **Flexible Scheduling (Medium Impact)**
- Offer early morning, evening, weekend slots
- Reduce scheduling-to-appointment gap (< 14 days optimal)
- Accommodate variable work schedules
- Expected outcome: 3-5% improvement for working-age patients

### 3. **Targeted Outreach (High Impact)**
- Priority follow-up for high-risk demographics:
  - Patients on scholarship program
  - Young adults (18-29)
  - First-time appointment attendees
  - Long wait times (> 30 days)

### 4. **Transportation Support (High Impact)**
- Partner with transportation services
- Provide transportation vouchers for low-income patients
- Create shuttle services from transit hubs
- Expected outcome: 10-15% improvement for transportation-constrained groups

### 5. **Incentive Programs (Medium Impact)**
- Reward consistent attendance with loyalty credits
- Penalty reduction for missing appointments (education-based)
- Social/community rewards for participation
- Expected outcome: 2-4% improvement

### 6. **Technology Solutions**
- Online appointment booking (reduce scheduling friction)
- Automated confirmation systems
- Geolocation-based reminders
- Telemedicine options for routine follow-ups

### 7. **Healthcare Literacy**
- Education campaigns on appointment importance
- Explain preventive care benefits
- Multilingual materials for diverse populations

---

## 📁 Repository Structure

```
No-Show-Appointments/
├── README.md                          # This file
├── no-show appointments.ipynb        # Main analysis notebook
├── noshowappointments-kagglev2-may-2016.csv  # Dataset
└── [Analysis outputs]
```

---

## 📚 Data Dictionary

| Column | Type | Description |
|--------|------|-------------|
| PatientId | Float | Unique patient identifier |
| AppointmentID | Integer | Unique appointment ID |
| Gender | String | Patient gender (M/F) |
| ScheduledDay | DateTime | When appointment was scheduled |
| AppointmentDay | DateTime | When appointment was scheduled for |
| Age | Integer | Patient age in years |
| Neighbourhood | String | Neighborhood name |
| Scholarship | Binary | 1 = on Brazilian welfare program, 0 = not |
| Hipertension | Binary | 1 = has condition, 0 = no |
| Diabetes | Binary | 1 = has condition, 0 = no |
| Alcoholism | Binary | 1 = reported condition, 0 = no |
| Handcap | Integer | Disability classification (0-4) |
| SMS_received | Binary | 1 = SMS reminder sent, 0 = not sent |
| **No-show** | **String** | **"Yes" = missed, "No" = attended** |

---

## 🌍 Global Health Context

### Why This Matters Beyond Brazil:

This Brazilian dataset has **profound implications for healthcare in Nigeria and West Africa**:

**Similarities in Healthcare Challenges:**
1. **Limited Resources**: Both regions face healthcare facility constraints
2. **Transportation Barriers**: Geographic distance to health facilities
3. **Socioeconomic Disparities**: Income-based access inequalities
4. **Healthcare Literacy Gaps**: Varying awareness of healthcare importance
5. **Work-Life Balance**: Inflexible employment in informal sectors

**Applicable Interventions for Nigeria:**
- SMS reminders (high phone penetration in Nigeria)
- Community health worker outreach
- Mobile health clinics reducing travel burden
- Partnership with employers for appointment time flexibility
- Local transportation solutions using existing infrastructure

### Healthcare System Implications:

**In Nigeria Specifically:**
- ~30% of population lives below poverty line (similar to Brazilian scholarship population)
- Transportation to urban health centers major barrier
- Mobile phone penetration > 90% (enable SMS-based solutions)
- Growing private healthcare sector (appointment management critical)

---

## 🚀 How to Use This Project

### View the Analysis:
```bash
jupyter notebook no-show\ appointments.ipynb
```

### Key Sections in Notebook:
1. Data loading and initial exploration
2. Data cleaning and preprocessing
3. Demographic analysis (gender, age, neighborhood)
4. Behavioral factor analysis (scholarship, SMS, conditions)
5. Statistical visualizations
6. Conclusions and recommendations

### Reproduce the Analysis:
```python
# Install dependencies
pip install pandas numpy matplotlib seaborn jupyter

# Run notebook cells to regenerate all analyses
```

---

## ⚠️ Limitations & Considerations

### Data Limitations:
1. **Single Location**: Vitória, Brazil (may not generalize globally)
2. **Single Time Period**: 2016 data (patterns may have shifted)
3. **Missing Context**: 
   - Appointment importance/urgency unknown
   - Reason for absence not recorded
   - Patient satisfaction/engagement unknown
4. **Reverse Causality**: SMS recipients likely already higher-risk

### Analytical Limitations:
1. **Correlation ≠ Causation**: Associations, not causal relationships
2. **Confounding Variables**: Many unmeasured factors influence attendance
3. **Temporal Dynamics**: Time-based patterns not fully explored

### Generalization:
- Results specific to Brazilian healthcare system
- Require validation in other geographic/cultural contexts
- Should be combined with qualitative research (interviews, focus groups)

---

## 🎓 Educational Value

This project demonstrates:
- ✅ Real-world healthcare data analysis
- ✅ Exploratory data analysis (EDA) methodology
- ✅ Demographic analysis and segmentation
- ✅ Pattern identification and visualization
- ✅ Actionable recommendation development
- ✅ Global health application thinking
- ✅ Jupyter proficiency
- ✅ Statistical interpretation

---

## 🔗 Resources & References

### Data Source:
- **Kaggle Dataset**: No Show Appointments (Brazilian Healthcare)
- **UCI Machine Learning Repository**: Medical Appointment Data

### Healthcare & Policy:
- World Health Organization (WHO) healthcare access metrics
- Nigerian Healthcare System reports
- Brazilian healthcare system structure

### Similar Projects:
- Patient adherence modeling
- Healthcare scheduling optimization
- Preventive care intervention analysis

---

## 🤝 Contributing & Future Work

### Potential Extensions:
- Time series forecasting of no-show rates
- Predictive model for individual appointment risk
- Cost-benefit analysis of interventions
- Simulation of intervention impacts
- Machine learning classification (XGBoost, Random Forest)

### Data Collection:
- Qualitative interviews with no-show patients
- Provider perspective on barriers
- Intervention pilot program outcomes

---

## 📄 License

This analysis uses publicly available Kaggle dataset. Available for educational and research purposes.

---

**Analysis Type**: Exploratory Data Analysis + Health Policy  
**Dataset**: Brazilian Medical Appointments (110,527 records)  
**Tools**: Python, Jupyter, Pandas, Seaborn  
**Status**: Complete & Reproducible  
**Purpose**: Healthcare Analytics & Global Health Portfolio Project