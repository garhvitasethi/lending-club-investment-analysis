# Data-Driven Investment Strategies for Peer-to-Peer Lending

## Project Overview

This project develops machine learning-based investment strategies for peer-to-peer lending using historical LendingClub loan data (2014-2015). The analysis demonstrates how data science techniques can guide investment decisions in P2P lending platforms, helping investors identify profitable loans while managing risk.

## Business Context

Peer-to-peer lending platforms like LendingClub connect borrowers with individual investors, offering potentially higher returns than traditional savings products. However, investors face the challenge of selecting loans from thousands of options with varying risk profiles. This project addresses the question: **Can data-driven strategies outperform simple heuristics or random selection in P2P lending?**

## Problem Statement

An investor (Jasmin) seeks to:
- Identify loans with high return potential and low default risk
- Develop a diversified portfolio that balances risk and return
- Outperform LendingClub's grade-based system through deeper analysis
- Make investment decisions based on data-driven insights rather than intuition

## Methodology & Analysis Pipeline

The project follows a comprehensive four-stage analytics pipeline:

### 1. Diagnostic & Descriptive Analysis
- **Data cleaning and preparation** of 2014-2015 LendingClub loan datasets
- **Feature engineering** including three return calculation methods (M1_PESS, M2_OPT, M3)
- **Exploratory Data Analysis (EDA)** revealing key default predictors:
  - Debt-to-income ratio (DTI < 20% preferred)
  - Revolving credit utilization (< 55% optimal)
  - Delinquency history
  - Loan purpose (debt consolidation more reliable)
- **Principal Component Analysis (PCA)** showing loan amount and installment drive variance
- **Clustering analysis** demonstrating that borrower segments don't align perfectly with LendingClub grades

### 2. Predictive Analysis & Simple Prescriptions
- **Classification models** to predict loan default probability:
  - Decision Trees
  - Logistic Regression (L1/L2 regularized)
  - Random Forest
  - Multilayer Perceptron
  - Naive Bayes
- **Regression models** to predict loan returns
- **Signal leakage prevention** by excluding post-issuance variables
- **Downsampling** to handle class imbalance (~15% default rate)
- **Simple investment strategies**:
  - Random selection (baseline)
  - Lowest default probability
  - Highest predicted returns
  - Combined analytical engineering approach

### 3. Prescriptive Analysis & Optimization
- **Risk assessment** using K-means clustering (20 clusters) to assign risk scores
- **Portfolio optimization** using integer programming:
  - Maximize total returns
  - Budget constraints
  - Markowitz-type risk-return models
- **Sensitivity analysis** on portfolio size and risk tolerance
- **Comparison** of optimization-based vs. rule-based strategies

### 4. Final Recommendation & Validation
- Performance evaluation across different portfolio sizes (100-1000 loans)
- Stability testing across different time periods
- Comprehensive strategy comparison

## Key Findings

### Investment Strategy Recommendations
**Primary Focus:** Grades B and C loans (balanced risk-return profile)
- Grade B loans: ~13% default rate, ~11% average interest
- Grade C loans: ~22% default rate, ~14% average interest

**Portfolio Composition:**
- Core allocation: Grades B and C (60-70%)
- Stability component: Grade A (15-25%)
- Yield enhancement: Grade D (5-10%)
- Avoid: Grades E, F, G (risk exceeds reward)

### Critical Risk Factors
- **DTI Ratio:** Target < 20%
- **Revolving Utilization:** Prefer < 55%
- **Delinquency History:** Avoid any recent delinquencies
- **Loan Purpose:** Debt consolidation shows higher reliability

### Performance Results
- Data-driven strategies **significantly outperform** random selection
- Two-stage analytical engineering strategy yields **best returns**
- Optimization-based portfolio selection provides **3-4% additional returns** over simple strategies
- Returns decrease with portfolio size (due to good loan scarcity)

## Dataset

**Source:** LendingClub historical loan data (archived via Wayback Machine)
- **Training Data:** LoanStats3d (2014 loans)
- **Test Data:** LoanStats3c (2015 loans)
- **Features:** 145+ variables including borrower characteristics, loan details, and credit history
- **Note:** FICO scores unavailable in archived data

## Repository Structure

```
├── README.md                          # This file
├── data/
│   ├── raw/
│   │   ├── LoanStats3d.csv           # 2014 loan data
│   │   └── LoanStats3c.csv           # 2015 loan data
│   └── README.md                      # Data description
├── notebooks/
│   ├── 01_diagnostic_and_descriptive_analysis.ipynb
│   ├── 02_diagnostic_and_descriptive_analysis_additional.ipynb
│   ├── 03_predictive_analysis_and_simple_prescriptions.ipynb
│   └── 04_prescriptive_analysis_and_final_recommendation.ipynb
├── references/
│   └── cohen_et_al_2018.pdf          # Academic paper providing theoretical foundation
└── LICENSE
```

## Technical Implementation

**Languages & Libraries:**
- Python 3.x
- Pandas, NumPy (data manipulation)
- Scikit-learn (machine learning models)
- Matplotlib, Seaborn (visualization)
- Gurobi/CPLEX (optimization)

**Key Techniques:**
- Feature engineering and selection
- Cross-validation and hyperparameter tuning
- Classification and regression modeling
- Clustering for risk assessment
- Integer programming for portfolio optimization
- Model calibration and evaluation (AUC, ROC curves)

## How to Use This Repository

1. **Explore the Analysis:** Each Jupyter notebook contains detailed explanations, code, and visualizations for every step of the analysis pipeline.

2. **Reproduce Results:** 
   - Download LendingClub data (links in data/README.md)
   - Run notebooks sequentially (01 → 04)
   - All preprocessing and modeling steps are documented

3. **Adapt for Your Use:**
   - Modify investment constraints in optimization notebooks
   - Test different model combinations
   - Apply to other P2P lending platforms

## Key Takeaways

**Data science adds value:** Machine learning strategies consistently beat random selection
**LendingClub grades are imperfect:** Deeper analysis reveals better loan selection criteria
**Optimization matters:** Portfolio optimization provides measurable improvement over simple rules
**Risk management is critical:** Diversification across grades and risk factors improves stability
**Scalability challenge:** Returns diminish as portfolio size increases (good loans are finite)

## Limitations & Considerations

- Analysis based on historical data (2014-2015); market conditions may have changed
- FICO scores unavailable in archived dataset
- LendingClub ceased P2P lending operations in 2020
- Results assume perfect information at time of investment
- Transaction costs and liquidity constraints not modeled

## Academic Context

This project is based on the case study by Cohen et al. (2018), "Data-Driven Investment Strategies for Peer-to-Peer Lending: A Case Study for Teaching Data Science" (*Big Data* journal). The reference paper is included in the `references/` directory.


## Acknowledgments

- Original case study by Cohen, Guetta, Jiao & Provost (2018)
- LendingClub for making historical data publicly available
- Internet Archive (Wayback Machine) for preserving the data

---

**Note:** This repository demonstrates the application of data science to real-world investment decisions. The strategies and findings should not be construed as financial advice. Past performance does not guarantee future results.
