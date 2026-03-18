# Advertising Effectiveness & Budget Optimization using AdStock Model

## Project Overview
This project analyzes the impact of advertising expenditure on retail sales using real-world data from The Warehouse (New Zealand retail company).

The objective is to evaluate both short-term and long-term effects of different advertising channels and develop a data-driven approach to optimize marketing budget allocation.

The analysis follows a full end-to-end workflow, including data preprocessing, exploratory data analysis, model development, and model optimization.

---

## Business Context
Retail companies invest across multiple advertising channels such as television, radio, and digital platforms. However, measuring the effectiveness of these channels is challenging due to:

- Delayed (lagged) effects of advertising  
- Differences in performance across channels  
- Influence of external factors such as holidays and weather  

This project aims to quantify these effects and support more effective marketing investment decisions.

---

## Dataset
- Source: The Warehouse internal dataset  
- Time Range: January 2017 – February 2020  
- Scope: 20 stores, 1155 observations :contentReference[oaicite:0]{index=0}  

### Key Variables

Sales:
- TotalSales (dependent variable)

Advertising Channels:
- Television  
- Radio  
- Digital  
- Mailer  
- Press  

External Factors:
- Holiday periods  
- Weather (temperature, rainfall)  

---

## Methodology

### 1. Data Preprocessing
- Cleaned dataset and removed extreme outliers  
- Applied filtering to exclude abnormal non-holiday values  
- Created holiday dummy variables to capture seasonal spikes  
- Standardized variables for modeling  

Holiday periods such as Christmas and New Year showed significant spikes in sales. Non-holiday extreme values were removed using a quartile-based approach to improve model stability :contentReference[oaicite:1]{index=1}.

---

### 2. Exploratory Data Analysis (EDA)
- Conducted time-series analysis to observe trends in sales and advertising  
- Examined distribution and variability of advertising spend  
- Identified patterns and anomalies across stores and time  

Key observations:
- Strong seasonal spikes during holiday periods  
- High variability in advertising spend across channels  
- Initial evidence of correlation between digital advertising and sales  

---

### 3. Baseline Model
A log-linear regression model was first developed:

LN_TotalSales ~ LN_Television + LN_Radio + LN_Digital + LN_Mailer + LN_Press

Results:
- Digital and television advertising showed significant positive effects  
- Model performance:
  - R² ≈ 0.244 :contentReference[oaicite:2]{index=2}  

Limitation:
- The model failed to capture delayed effects of advertising  

---

### 4. AdStock Model (Lag Effect Modeling)
To address lag effects, AdStock transformation was applied to all advertising channels.

- Decay parameter (lambda): 0.9  
- Interpretation:
  - Advertising impact persists over time and decays gradually  

Results:
- R² improved to ≈ 0.3178 :contentReference[oaicite:3]{index=3}  
- Digital advertising demonstrated the strongest cumulative effect  

---

### 5. Feature Engineering and Model Enhancement

#### (1) Control Variables
- Added holiday dummy variables (2018–2020)  
- Purpose:
  - Isolate advertising effects from seasonal demand spikes  

Result:
- Slight improvement in model performance  

---

#### (2) Interaction Effects
Introduced interaction terms to capture real-world complexity:

- Cross-channel interactions:
  - Television × Digital  
  - Radio × Press  

- External interactions:
  - Television × Rainfall  
  - Digital × Temperature  

Results:
- R² improved to ≈ 0.3462 :contentReference[oaicite:4]{index=4}  

Insights:
- Strong synergy between TV and digital advertising  
- Advertising effectiveness varies under different external conditions  

---

#### (3) Parameter Optimization (Advanced)
Developed a SAS macro to optimize AdStock decay parameters:

- Iterated through combinations of lambda values (0.0–0.9)  
- Objective:
  - Maximize adjusted R²  

Best result:
- Lambda = (0.9, 0.9, 0.9, 0.9, 0.9)  
- Adjusted R² ≈ 0.3148 :contentReference[oaicite:5]{index=5}  

Interpretation:
- Advertising effects are highly persistent across all channels  

---

### 6. Elasticity Analysis
Calculated both short-term and long-term elasticity to quantify advertising impact.

Key findings:

Digital advertising:
- Short-term elasticity: 0.2754  
- Long-term elasticity: 2.7535  

Interpretation:
- Digital advertising delivers the strongest long-term return on investment  

---

## Key Findings

- Digital advertising has the highest long-term impact on sales  
- Advertising effects are cumulative rather than immediate  
- Cross-channel strategies significantly improve effectiveness  
- External factors such as holidays and weather influence performance  
- Traditional channels (TV, radio) remain effective when combined with digital  

---

## Business Recommendations

- Increase investment in digital advertising due to strong long-term returns  
- Leverage cross-channel strategies, especially TV and digital integration  
- Continuously optimize campaigns using data-driven approaches  
- Incorporate external factors such as seasonality and weather into planning  

---

## Tools and Technologies

- SAS (data processing and modeling)  
- Regression analysis  
- AdStock modeling  
- Time-series analysis  
