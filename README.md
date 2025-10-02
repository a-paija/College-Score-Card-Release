
<h1>Data Exploration Project: College Scorecard & Google Trends</h1>

<h2>Description</h2>

[This project](https://github.com/a-paija/College-Score-Card-Release/blob/main/College%20Scorecard%20Analysis.html) investigates whether the release of the **College Scorecard** in September 2015 influenced student interest in high-earning colleges relative to low-earning ones. Google Trends data is used as a proxy for student search interest. The analysis uses a **Difference-in-Differences (DiD) approach** to visualize this effect.

## Analysis Workflow

1. **Data Cleaning & Preparation**  
   - Imported raw data and standardized Google Trends indices (`index_z`).  
   - Merged with Scorecard data using the mapping file.  
   - Filtered and aggregated data for analysis by date and earnings group.

2. **Difference-in-Differences Model**  
   ```r
   did_model <- feols(
     index_z ~ treatment_group * post_policy + i(month_num, ref = 1) | schname,
     data = clean_data
   )

 - Interaction coefficient: -0.061

 - Standard Error: 0.02

 - Analysis: High-earning schools experienced a relative decline of 0.061 standard deviations in search interest compared to low-earning schools after the Scorecard release (p ≈ 0.0023).
 - Interpretation: After the release of the College Scorecard, student interest in high-earning colleges decreased slightly compared to low-earning colleges. This change is statistically significant, indicating that the Scorecard may have shifted attention away from higher-earning schools

3. Findings

![DiD Model](https://github.com/a-paija/College-Score-Card-Release/blob/main/DiD%20Model.png)

 - Pre-trends: Both groups show similar search interest before September 2015.

 - Post-release: Relative search interest in high-earning colleges decreased.

 - Possible explanations: increased awareness of selectivity/cost, revealed attractive features of lower-earning schools, or high-earning schools already well-known.

---

<h2>Insights</h2>

1. Awareness vs. Reinforcement

  - High-earning schools were likely already well-known brands (Ivies, flagships, elite privates). The Scorecard might have just reinforced that, so marginal search interest didn’t grow.
  - Low-earning schools may have gained visibility if they performed well on other Scorecard metrics (completion, affordability, diversity).


2. Market Dynamics in Higher Education

  - A small but significant behavioral shift (-0.061 SD) at scale could alter application patterns, enrollment demand, and revenue flows.
  - If students shift attention toward lower-earning but affordable schools, elite schools might see less incremental demand, while regional/state schools gain traction.
    
---

<h2>Recommendations</h2>

1.  Emphasize value metrics (earnings relative to cost, debt repayment rates), not just raw earnings.

2.  Improve usability of Scorecard so students interpret data correctly.

For High-Earning Colleges (Elites):

 - Double down on communicating career outcomes + scholarships, countering perceptions of unaffordability.

For Lower-Earning Colleges (Regionals/Community):

 - Highlight affordability, accessibility, and unique strengths — Scorecard data may help reposition them positively.

