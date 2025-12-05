# Lending club analysis
Lending Club operates as America's largest peer-to-peer lending marketplace, connecting borrowers seeking personal loans ($1,000-$40,000) with investors looking for attractive returns. The platform assigns risk grades (A through G) based on creditworthiness, with interest rates ranging from 6% to 36%. Between 2007-2018, Lending Club originated over $50 billion in loans. This analysis examines 1.35 million completed loans from the company's historical portfolio to identify optimization opportunities in product mix and risk management.

### Data Architecture

**Normalized SQLite Database:**
- `dim_loan_products`: Loan characteristics (grade, term, amount, interest rate)
- `dim_borrowers`: Borrower profiles (FICO, DTI, employment)
- `fact_loan_performance`: Loan outcomes and performance metrics

**Dataset:**
- **Records:** 1,347,721 loans
- **Time Period:** 2007-2018
- **Source:** Lending Club company (historical real world data) 
- **Size:** 1.35M records across 3 normalized tables

-1,347,721 loans analyzed across 14 segments (7 grades × 2 terms) $3.17B total profit generated 16.3% average ROI with 29.7% default rate

  <img width="856" height="476" alt="image" src="https://github.com/user-attachments/assets/19aa0d00-0798-401b-b671-ef23411d2b56" />
### Key Insights

**Portfolio Performance & Opportunities** 
Portfolio exhibits significant term structure imbalance. Extended-term products (60 months) generate 183% higher profit per loan ($4,626 vs $1,632) yet represent only 24% of origination volume. This structural underweight in high-performing segments suggests potential value creation of $700M+ through strategic rebalancing.
The top tier—60-month loans—consistently delivers $4,000-$5,200 profit per loan. The bottom tier—36-month loans—clusters around $800-$2,000. Yet 76% of capital flows to the lower-performing tier.
Grade B-C borrowers at 60-month terms emerge as clear winners: $5,000+ profit per loan, 25%+ returns, proven volume of 153K loans. One segment stands out negatively: Grade G-36m loses $662 per loan. While small in absolute volume, it represents systematic value destruction.

**Insights Deep-Dive**
60-month loans average $4,626 profit with 323,492 originations, representing 24% of portfolio volume.
36-month loans average $1,632 profit with 1,024,229 originations, representing 76% of portfolio volume.
All seven risk grades perform 150-200% better at 60-month term, indicating systematic underweighting rather than segment-specific anomaly.
Extended terms accumulate more interest revenue over life of loan, with default risk increasing more modestly than revenue gain.

### Risk model

<img width="849" height="311" alt="image" src="https://github.com/user-attachments/assets/353500a5-9e6d-4ab6-b5f9-600aa1aa3350" />

**Composite risk score (4-13) demonstrates strong predictive power:**

- **Score 4 (Lowest Risk):** shows 4.8% default but constitutes only 308K loans (23% of volume), suggesting potential underweight in safest segments.
- **Score 8 (Moderate Risk):** 20.2% default, 308K loans (largest segment)
- **Score 13 (Highest Risk):** 60.5% default, 1K loans
- **High-risk tail (scores 11-13) represents 5% of portfolio with 50%+ default rates, demonstrating controlled exposure to elevated-risk segments.**
- **12.5x separation** between lowest and highest risk

The risk model tells two stories. 
First, it works—default rates climb smoothly from 4.8% (low risk) to 60.5% (high risk) with no inversions. Second, the portfolio concentrates in the middle: 72% concentrated in moderate risk (scores 7-10), with largest single segment at score 8 (308K loans).

**Grade B-C Profitability Leadership**
Grade B-60m generates $5,258 average profit per loan (25.8% ROI) with 47,808 originations.
Grade C-60m generates $4,925 average profit per loan (24.9% ROI) with 105,553 originations.
Combined B-C 60-month segments represent only 11.4% of portfolio despite ranking #1 and #2 in profitability.
These moderate-risk segments balance volume scalability with superior risk-adjusted returns.

---
### Economic Cycle Behavior

<img width="828" height="445" alt="image" src="https://github.com/user-attachments/assets/ae18304c-6a23-48d9-bba8-26a9a99ddffb" />

**2007-2008 Financial Crisis impact analysis:**
2007 originations peaked at 26% average default across all grades during financial crisis.
Default rates declined to 13-15% by 2009-2010, demonstrating 24-month recovery period.
Post-2015 portfolio stabilized at 18-22% normalized default range.
All grades moved directionally together during crisis (+60-80% relative increase) while maintaining risk hierarchy, with no grade inversions observed throughout cycle.
**2-year recovery period** demonstrates portfolio resilience
**Risk Management Validation:** Model maintained predictive power across economic cycles. 

**Recommendations**
**Portfolio Optimization**

Increase 60-Month Allocation: Gradually shift portfolio mix from current 24% to target 40-45% in 60-month products over 12-18 months. Implement through marketing channel optimization, pricing incentives for extended terms, and borrower education campaigns emphasizing payment flexibility benefits.
Reprice Grade A-36m: Current 14.2% ROI falls below portfolio average of 16.3% despite lowest risk profile. Evaluate rate increases of 100-150 basis points or introduce incentive structure to migrate borrowers to 60-month products where Grade A achieves 24.2% ROI.
Exit Grade G-36m: Discontinue originations for only segment with negative economics (-$662 per loan, -4.6% ROI). Redirect underwriting capacity and capital to positive-return segments. Expected impact: +$7M value plus risk reduction benefits.

**Growth and Scale**

Expand Grade B-C 60-Month Volume: Increase originations by 50% from current 153K annual loans to ~230K. Focus marketing, sales incentives, and credit box refinement on these highest-performing segments. Target portfolio weight increase from 11.4% to 15-18%.
Optimize Term Mix Messaging: Develop borrower communication strategy highlighting total interest savings and credit building benefits of extended terms. Test pricing bundles, promotional periods, and partnership channels to accelerate 60-month adoption rates.

**Risk Management Enhancement**

Refine Risk-Based Pricing: Current wide profitability variance across segments (ranging from -4.6% to 25.8% ROI) suggests opportunity for granular pricing optimization. Implement enhanced scoring models incorporating additional behavioral and macroeconomic variables.
Strengthen Economic Preparedness: Historical 24-month crisis recovery period provides benchmark for stress testing. Validate current 72% moderate-risk positioning against recession scenarios. Develop countercyclical playbook including tightening triggers, portfolio rebalancing protocols, and capital cushion requirements.

**Tools & Technologies**

| Category | Tools | Purpose |
|----------|-------|---------|
| **Database** | SQLite | Data storage & normalization |
| **Analysis** | SQL (Window functions, CTEs, aggregations) | Complex analytical queries |
| **Data Processing** | Python (pandas) | Data export & transformation |
| **Visualization** | Power BI Desktop | Interactive dashboards |

⭐ If you found this analysis valuable, please star this repository!
