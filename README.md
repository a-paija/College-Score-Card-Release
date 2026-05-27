## 🟦 Project Background
This project investigates whether the College Scorecard release (September 2015) influenced student interest in high-earning vs. low-earning colleges. Using Google Trends data as a proxy for student search behavior, the analysis applies a Difference-in-Differences (DiD) framework to estimate the causal impact of increased transparency in college outcomes.

## 🟦 Analysis Workflow
### 1. Data Cleaning & Preparation
- Imported and cleaned raw datasets  
- Standardized Google Trends indices (index_z)  
- Merged Trends data with College Scorecard using a mapping file  
- Aggregated data by date and earnings group  

### 2. Difference-in-Differences Model
    did_model <- feols(
      index_z ~ treatment_group * post_policy + i(month_num, ref = 1) | schname,
      data = clean_data
    )

### Key Results
- Interaction Coefficient: -0.061  
- Standard Error: 0.02  
- p-value: ≈ 0.0023  

### Interpretation
High-earning schools experienced a relative decline of 0.061 standard deviations in search interest compared to low-earning schools after the Scorecard release. This effect is statistically significant, suggesting the Scorecard shifted attention away from traditionally high-earning institutions.

## 🟩 Findings
![DiD Model](https://github.com/a-paija/College-Score-Card-Release/blob/main/DiD%20Model.png)
- Pre-Trends: Parallel movement between groups before September 2015  
- Post-Release: Decline in relative search interest for high-earning schools  
- Potential Drivers: Increased awareness of cost vs. earnings trade-offs, greater visibility of affordable institutions, and already high baseline awareness for elite schools  

## 🟨 Insights
### Awareness vs. Reinforcement
- High-earning schools (elite/private institutions) were already well-known  
- The Scorecard likely reinforced existing perceptions rather than expanding interest  
- Lower-earning schools may have gained visibility through affordability, completion rates, and accessibility  

### Market Dynamics in Higher Education
- A -0.061 SD shift, while small, is meaningful at scale  
- Potential downstream impacts include changes in application distribution, enrollment patterns, and revenue allocation  
- Indicates a shift toward value-driven decision-making among students  

## 🟥 Recommendations
### For Policymakers / Scorecard Designers
- Emphasize value-based metrics (earnings relative to cost, debt outcomes)  
- Improve usability to ensure correct interpretation  

### For High-Earning Colleges (Elite Institutions)
- Strengthen communication around career outcomes and financial aid  
- Address perception of high cost limiting accessibility  

### For Lower-Earning Colleges (Regional / Community)
- Highlight affordability, accessibility, and career pathways  
- Use Scorecard data to reposition institutional value  

## 🟦 Key Takeaway
The College Scorecard did not increase interest in high-earning schools; instead, it shifted student attention toward more affordable and accessible institutions, signaling a measurable change in decision-making behavior.
