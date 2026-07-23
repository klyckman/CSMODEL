## MCO2 Notebook Changes

Updated notebook: `Kodiak_Knowers_MCO2.ipynb`

### Research Direction

- Updated the refined research question to:

  > Which social-media-use patterns are associated with focus difficulty among young adults?

- Continued using only `smmh.csv`.
- All EDA, data-mining, and inference results use the same 371 respondents.
- The other two datasets are not loaded, partially analyzed, or combined.
- No missing focus values were imputed.

### Data-Mining Section

Added Association Rule Mining as the required data-mining technique.

Respondents were represented as transactions containing these binary items:

- `High time`: at least 4.5 mapped social-media hours
- `High purposeless use`: response of 4–5
- `High restlessness`: response of 4–5
- `High focus difficulty`: normalized score of at least 0.75

Mining thresholds:

- Minimum support: `0.15`
- Minimum confidence: `0.60`

Implemented:

- Generation of one-, two-, and three-item frequent itemsets
- Calculation of support counts and proportions
- Generation of rules with `High focus difficulty` as the consequent
- Calculation of rule confidence
- Visualization comparing support and confidence

Rules that met both thresholds:

| Association rule | Support | Confidence |
|---|---:|---:|
| High restlessness → High focus difficulty | 0.183 | 0.660 |
| High purposeless use + high restlessness → High focus difficulty | 0.151 | 0.747 |

### Statistical-Inference Setup

Added:

- `scipy.stats` for course-taught statistical tests
- A significance level of `α = 0.05`
- Q-Q plots for checking group distributions
- Central Limit Theorem justification for large groups
- Group-size and standard-deviation checks

Created the following analysis groups:

- Social-media time: low, moderate, and high
- Purposeless use: low, neutral, and high
- Restlessness: low, neutral, and high
- Focus difficulty: high or lower

### Statistical Test 1: Social-Media Time and Focus

Applied one-way ANOVA to compare mean focus difficulty across time groups.

Results:

- `F = 8.593`
- `p = 0.000225`
- The null hypothesis of equal means was rejected.

Added Bonferroni-adjusted pairwise t-tests:

- Low versus moderate: not significant (p ≈ 0.03163, exceeds adjusted α ≈ 0.0167)
- Low versus high: significant (p ≈ 0.00005)
- Moderate versus high: not significant (p ≈ 0.18401)

The primary difference occurred between low-use respondents and high-use respondents; moderate use was not clearly distinguishable from either group.

### Statistical Test 2: Purposeless Use and Focus

Applied one-way ANOVA to compare mean focus difficulty across purposeless-use groups.

Results:

- `F = 29.623`
- `p ≈ 1.18 × 10⁻¹²`
- The null hypothesis of equal means was rejected.

Bonferroni-adjusted comparisons:

- Low versus high: significant
- Neutral versus high: significant
- Low versus neutral: not significant after correction

The high purposeless-use group had the clearest difference in focus difficulty.

### Statistical Test 3: Restlessness and Focus

Applied a chi-square test of independence between restlessness group and focus-difficulty category.

Results:

- `χ² = 56.949`
- Degrees of freedom: `2`
- `p ≈ 4.30 × 10⁻¹³`
- Minimum expected count: `38.35`

The null hypothesis of independence was rejected. Respondents with higher restlessness were more likely to belong to the high-focus-difficulty category.

### Summary and Conclusion Updates

Updated the final sections to connect the EDA, data-mining, and inference findings.

Main conclusion:

- Time spent on social media has a limited relationship with focus difficulty.
- Purposeless use has a stronger relationship with focus difficulty.
- Restlessness has the strongest and most consistent relationship across EDA, association-rule mining, and statistical inference.
- The results show association and co-occurrence, not causation.

Also expanded:

- Study limitations
- Interpretation of the constructed focus score
- Effects of categorization and threshold choices
- Recommendations for more intentional social-media use
- Recommendations for future research using validated focus measures and longitudinal data

### Notebook Validation

The MCO2 review notebook currently contains:

- 71 total cells
- 25 code cells
- 2,534 Markdown words
- 6 figures
- No Markdown cell exceeding 100 words
- No saved execution errors
- No saved warning outputs

The notebook was executed successfully from top to bottom. It remains an uncommitted review copy and should be examined and rewritten by the group before submission.