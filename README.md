# **A/B Testing, Done Properly: Cookie Cats Gate Placement**

## **Project Overview**

A validity-first A/B testing analysis of the Cookie Cats mobile game dataset, covering 90,189 players to evaluate the impact of moving the first progression gate from level 30 to level 40 on player retention.

The project goes beyond basic hypothesis testing by validating the experimental split, investigating outliers, measuring effect sizes, calculating statistical power, simulating false-positive inflation from repeated testing, and correcting for multiple comparisons across player segments.

**Key Result:** Moving the gate to level 40 was associated with a **0.82 percentage-point decrease in 7-day retention** (p = 0.0016). Although the overall effect was small (Cohen's h = 0.021), the decline was larger among highly engaged players.

**Business Recommendation:** Do not ship `gate_40` based on the current evidence. Investigate the sample ratio mismatch before making a final product decision.

## **Key Findings**

- **Experiment Validity:** Detected a potential sample ratio mismatch (SRM), with a chi-square statistic of 6.90 and p = 0.0086.
- **1-Day Retention:** Observed a difference of 0.59 percentage points, which was not statistically significant (p = 0.0744).
- **7-Day Retention:** Retention was 19.02% for `gate_30` versus 18.20% for `gate_40` (p = 0.0016).
- **Effect Size:** Cohen's h of 0.021 indicates a small overall standardized effect.
- **Outlier Analysis:** Identified one player with 49,854 game rounds and excluded the observation from the mean-based rounds analysis.
- **Statistical Power:** Estimated a minimum detectable effect of approximately 0.73 percentage points at 80% power.
- **Peeking Simulation:** Repeated significance testing increased the simulated false-positive rate from 4.7% to 25.0%.
- **Segment Analysis:** Engagement quartiles Q3 and Q4 showed significant retention differences after Benjamini–Hochberg correction.

## **Methodology**

1. **Data Validation:** Checked sample allocation using a chi-square SRM test and investigated extreme values.
2. **Power Analysis:** Estimated the minimum detectable effect using the available sample size.
3. **Hypothesis Testing:** Applied two-proportion z-tests for retention and the Mann–Whitney U test for game rounds.
4. **Effect Size Estimation:** Used Cohen's h, rank-biserial correlation, and bootstrap confidence intervals.
5. **Peeking Simulation:** Simulated repeated significance testing to demonstrate optional-stopping risks.
6. **Segment Analysis:** Compared retention across engagement quartiles and applied Benjamini–Hochberg false discovery rate correction.

## **Tools & Technologies**

- Python
- Pandas
- NumPy
- SciPy
- Matplotlib
- Seaborn
- Statistical Hypothesis Testing
- A/B Testing
- Bootstrap Resampling
- Permutation Testing
- Statistical Power Analysis

## **Business Impact**

This project demonstrates how rigorous experimental analysis can help product teams avoid misleading conclusions, identify potential data-quality issues, quantify the practical significance of product changes, and make evidence-based decisions about player retention and game progression.

**Key Takeaway:** A reliable A/B test requires more than a statistically significant p-value. Experiment validity, effect sizes, uncertainty, multiple testing, and business impact must all be considered before shipping a product change.
