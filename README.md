# econ5200-lab01-data-portfolio

## Data Quality Profiling — Big Mac Index

### Objective
This project audits the Economist's Big Mac Index dataset for structural and 
computational data quality issues, correcting a purchasing power parity (PPP) 
calculation error and quantifying the effect of survivorship bias introduced 
by incomplete country panels.

### Methodology
- Diagnosed a PPP computation error caused by a swapped numerator/denominator 
  in the exchange-rate ratio, and corrected the formula
- Identified a survivorship bias risk: restricting analysis to countries with 
  complete time-series panels systematically excludes markets that entered 
  or exited coverage, skewing the sample toward more stable economies
- Quantified the bias by comparing the complete-panel average Big Mac price 
  against the all-available average across all periods
- Built `profile_dataframe()`, a reusable diagnostic function that reports 
  dataset structure (unit and period counts), panel completeness/balance, 
  and per-column missing-value percentages

### Key Findings
- The complete-panel average Big Mac price was $0.081 (+2.1%) higher than 
  the all-available average, indicating that restricting to complete panels 
  overstates typical prices
- This premium held in 33 of 45 periods, suggesting the bias is persistent 
  rather than driven by a few outlier periods
- Together, these findings show that naive panel-completeness filtering can 
  materially distort cross-country price comparisons if not corrected for
