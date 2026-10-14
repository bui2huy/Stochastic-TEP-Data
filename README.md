# Dataset for Stochastic Transmission Expansion Planning

**Authors:** Nguyen Duc Huy Bui, Thanh Long Duong

## Overview
This repository provides the comprehensive input data utilized for stochastic transmission expansion planning (TEP) models under high penetrations of renewable energy sources. The dataset ensures strict computational reproducibility for associated grid infrastructure research.

## Data Structure
The provided dataset (`RESs data.xlsx`) includes 24-hour chronological load scaling factors and 10 representative stochastic scenarios for both wind and solar power generation, alongside their precise probability weights. 

The dataset is organized into two primary spreadsheets corresponding to two standard benchmark test systems: Garver 6-bus and IEEE 118-bus systems.

## Data Standardization
To ensure scalability and seamless integration into computational frameworks, all time-series data and generation trajectories are standardized in per-unit (pu) values.

## Sensitivity Analysis of the Fictitious Generator Dispatch Threshold

In the proposed framework, ESS locations are preselected rather than optimized through binary investment decisions. A fictitious generator dispatch threshold of \(10^{-4}\) is used to identify candidate locations while avoiding the selection of negligible dispatch values that may arise from numerical solver tolerances. The following sensitivity analysis examines the effect of this threshold on ESS candidate selection and the resulting planning decisions, providing additional justification for the selected value.

### Table 1. Sensitivity of ESS Deployment to the Candidate Siting Threshold under Case D2

| Metric | \(10^{-2}\) | \(10^{-4}\) | \(10^{-6}\) |
|:---|---:|---:|---:|
| Number of candidate locations | 24 | 24 | 24 |
| Number of candidates passing the \(P_i^{ESS}\) and \(E_i^{ESS}\) threshold | 15 | 15 | 23 |
| Number of installed ESS units | 15 | 15 | 15 |
| Total installed power (MW) | 364.285 | 364.285 | 364.285 |
| Total installed energy (MWh) | 606.72 | 606.72 | 606.72 |
| Total annual cost (M$/year) | 17.5886 | 17.5886 | 17.5886 |

### Discussion

The final planning results remain unchanged across the three threshold values. Reducing the threshold from \(10^{-4}\) to \(10^{-6}\) increases the number of candidate locations passing the initial \(P_i^{ESS}\) and \(E_i^{ESS}\) screening from 15 to 23. However, the number of installed ESS units, total installed power and energy capacities, and total annual cost remain unchanged. This is because the additional candidates are subsequently rejected by the economic criterion (criterion (ii) in Equation (44) of the manuscript), as their fixed installation costs exceed the corresponding reductions in LOLC.

The two criteria therefore serve complementary purposes: criterion (i) screens out negligible ESS capacities, whereas criterion (ii) prevents economically unjustified installations. For example, an EENS reduction of only \(10^{-4}\) MWh/day would require a VoLL exceeding approximately 408,000 $/MWh to offset an annualized fixed ESS cost of 0.0149 M$/year, assuming that the deficit is completely eliminated. This estimate is based on an ESS capital cost of 0.1 M$ and an annualization factor of approximately 0.1490, and is well above the VoLL range considered in this study (0–12,000 $/MWh).

These results support the selection of \(10^{-4}\) as a reasonable threshold for the cases investigated. The sensitivity analysis is provided to further substantiate this choice and facilitate reproducibility.
